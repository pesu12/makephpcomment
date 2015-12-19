[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/pesu12/makephpcomment/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/pesu12/makephpcomment/?branch=master)

[![Code Coverage](https://scrutinizer-ci.com/g/pesu12/makephpcomment/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/pesu12/makephpcomment/?branch=master)

[![Build Status](https://scrutinizer-ci.com/g/pesu12/makephpcomment/badges/build.png?b=master)](https://scrutinizer-ci.com/g/pesu12/makephpcomment/build-status/master)


PHP MakePhpComment Module
==========================

PHP MakePhpComment Nov 2015 by Per Sundberg 


Introduction
------------
This is a module that uses the framework Anax-MVC Content CTextFilter
to format a textstring to a php-comment. 

Requirement
-----------

This library package requires PHP 5.3 or later.

Installation and Usage
----------------------
Install the ANAX-MVC from github on address:

git clone https://github.com/mosbth/Anax-MVC.git

Install the module php-makecomment to folder ANAX-MVC\3pp.

The php-makecomment is meant to be used with class autoloading. 
Therefore the Anax-MVC\app\config\autoloader.php needs to be updated with:

`->addNameSpace('pesu', ANAX_INSTALL_PATH . '3pp/php-makecomment/pesu')`

The file Anax-MVC\src\Content\CTextFilter.php needs to add after row 'shortcode' => 'shortCode',
with
`'phpcomment' => 'phpcomment',`  

The file Anax-MVC\src\Content\CTextFilter.php  needs to have function added.   

`public function phpcomment($text)
{
   return \pesu\MakePhpComment::makephpcomment($text);
}`


Add following to the ANAX-MVC/webroot/hello_view.php after $app->views->add('welcome/hello_world');

`$app->router->add('', function() use ($app) {
	$content = $app->textFilter->doFilter('Function: Test php comment\n\n@param
    string $text xxxx\n\n@return string text xxxx','shortcode, phpcomment');
    $app->views->add('welcome/page', [
        'content' => $content,
    ]);
});$app->router->handle();`
 
To the view file Anax-MVC\app\view\welcome add a file page.tpl.php with content:
<article class="article1">

`<?=$content?>

<?php if(isset($byline)) : ?>

<footer class="byline">

<?=$byline?>

</footer>

<?php endif; ?>

</article>`
 
Bugs
----

To file bug reports please send email to:
<sundberg_p@yahoo.com>

Development
-----------------------
This module has been developed at Blekinge Tekniska Högskola at Karlskrona Sweden
and is a part of course DV14886 PHP MVC.

Version History
---------------
PHP MakePhpComment Module 1.0.0 (22 Nov 2015), First Version

PHP MakePhpComment Module 1.0.1 (10 Dec 2015), Badges Added for Scrutinizer,coverage and build

Copyright and License
---------------------
PHP MakePhpComment Module

Copyright (c) 2015 Per Sundberg  
