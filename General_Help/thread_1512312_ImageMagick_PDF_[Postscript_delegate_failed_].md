---
title: "ImageMagick PDF [Postscript delegate failed ]"
date: 2010-06-18
forum: General Help
---

### Post by mech7 on 2010-06-18
I installed Imagemagick extension for PHP... but on some PDF I get this error..


Fatal error: Uncaught exception 'ImagickException' with message 'Postscript delegate failed `/WebsZone/WebsZone/flipbooksoft.com/public/test/test.pdf': No such file or directory @ pdf.c/ReadPDFImage/612' in /WebsZone/WebsZone/flipbooksoft.com/public/test/page.php:4 Stack trace: #0 /WebsZone/WebsZone/flipbooksoft.com/public/test/page.php(4): Imagick->__construct('test.pdf') #1 {main} thrown in /WebsZone/WebsZone/flipbooksoft.com/public/test/page.php on line 4

My script..

[PHP]<?php
error_reporting(E_ALL | E_STRICT);
ini_set("display_errors", 1);
$im = new imagick('test.pdf');
$max = $im->getNumberImages();    
echo 'pages: '.$max;
$im = new imagick('test.pdf');
$max = $im->getNumberImages();    
echo 'pages: '.$max;[/PHP]

Does anybody know what is wrong? The same file works on CentOS with ImageMagick..

Ubuntu:
GPL Ghostscript 8.70 (2009-07-31)
ImageMagick 6.5.1-0 2009-08-27 Q16 OpenMP

Centos:
ImageMagick 6.6.1-7 2010-05-13 Q16 
GPL Ghostscript 8.71 (2010-02-10)

Is it a bug in older ImageMagick? I rather not compile by myself  after many disasters compile by my own in CentOS  :mad:

---

