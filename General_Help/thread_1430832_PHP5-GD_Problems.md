---
title: "PHP5-GD Problems?"
date: 2010-03-15
forum: General Help
---

### Post by ubuntüser on 2010-03-15
"The image "xxx.xxx.xxx.xxx/test.php" cannot be displayed because it contains errors".

I'm trying to generate an image using php5-gd.
I have ubuntu server 9.10 installed with lamp stack. I have the php5-gd from apt repositories.

Is there any way I can fix this without compiling php5 from source?

EDIT: Some images work and some don't.

This one works:

[PHP]<?php
 
// example1.php
 
// set the HTTP header type to PNG
header("Content-type: image/png"); 
 
// set the width and height of the new image in pixels
$width = 350;
$height = 360;
 
// create a pointer to a new true colour image
$im = ImageCreateTrueColor($width, $height); 
 
// sets background to red
$red = ImageColorAllocate($im, 255, 0, 0); 
ImageFillToBorder($im, 0, 0, $red, $red);
 
// send the new PNG image to the browser
ImagePNG($im); 
 
// destroy the reference pointer to the image in memory to free up resources
ImageDestroy($im); 
 
?>[/PHP]

This one doesn't:

[PHP]<?php
 
// example5.php
 
// set the HTTP header type to PNG
header("Content-type: image/png"); 
 
// set the width and height of the new image in pixels
$width = 350;
$height = 360;
 
// create a pointer to a new true colour image
$im = ImageCreateTrueColor($width, $height);
 
// switch on image antialising if it is available
ImageAntiAlias($im, true);
 
// sets background to white
$white = ImageColorAllocate($im, 255, 255, 255); 
ImageFillToBorder($im, 0, 0, $white, $white);
 
// define black and blue colours
$black = ImageColorAllocate($im, 0, 0, 0);
$blue = ImageColorAllocate($im, 0, 0, 255);
 
 
function drawDiamond($x, $y, $width, $colour, $filled) {
    // access the global image reference (the one outside this function)
    global $im;
 
    // here we work out the four points of the diamond
    $p1_x = $x;
    $p1_y = $y+($width/2);
 
    $p2_x = $x+($width/2);
    $p2_y = $y;
 
    $p3_x = $x+$width;
    $p3_y = $y+($width/2);
 
    $p4_x = $x+($width/2);
    $p4_y = $y+$width;
 
    // now create an array of points to store these four points
    $points = array($p1_x, $p1_y, $p2_x, $p2_y, $p3_x, $p3_y, $p4_x, $p4_y);
 
    // the number of vertices for our polygon (four as it is a diamond
    $num_of_points = 4;
 
    if ($filled) {
        // now draw out the filled polygon
        ImageFilledPolygon($im, $points, $num_of_points, $colour);
    }else{
        // draw out an empty polygon
        ImagePolygon($im, $points, $num_of_points, $colour);
    }
}
 
// now draw the two diamonds
drawDiamond(120, 50, 100, $black, false);
drawDiamond(120, 200, 100, $blue, true);
 
// send the new PNG image to the browser
ImagePNG($im); 
 
// destroy the reference pointer to the image in memory to free up resources
ImageDestroy($im); 
 
?>[/PHP]

These are just test images to see whats working and what is not.

---

### Post by ubuntüser on 2010-03-15
I found out that I am missing some functions by using the one in the apt-get repositories:

Source: [http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)

Quote:  > The apt-get method will NOT work if you want to have a BUNDLED version of GD. The bundled version comes with thingies like “imagerotate” which is missing from the apt-got library. I am currently compiling the library, fingers crossed

Is there any way to get those advanced features without compiling from source?

---

### Post by fragos on 2010-03-15
I run a Desktop and installed Lamp with Synaptic and the Mark Packages by Task feature and had no trouble other than needing to enable PHP in httpd.conf. Apt-get doesn't do as complete a job with dependencies as the Gnome level application installers on some distros.

---

### Post by ubuntüser on 2010-03-15
The basic GD features work (like the captcha in phpbb3), but some features don't work.
Specifically, I'm trying to generate a forum signature using xlrstats.

---

### Post by ubuntüser on 2010-03-16
Does anybody have an answer? I saw from reading other forums, etc, that I'll need to compile my own version of PHP. But I don't want to do that. Its much easier to have an apt-get version of everthing.

---

### Post by ubuntüser on 2010-03-16
OK, I compiled php myself - used this guide:
[http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)

It works now.

---

### Post by saivert on 2011-01-14
I'm running Ubuntu Server 10.10 and the php5-gd package doesn't work with Drupal7. It can't locate GD..

this has to be fixed.

---

### Post by Nozzie on 2011-02-03
I also ran into the problem of missing functions in php5-gd.
There is a way to solve it, without recompiling php.
The original howto is located here: [http://memcloud.com/note/show/53](http://memcloud.com/note/show/53)
I have written my own, slightly modified version here: [http://nossie.addicts.nl/php5-gd.html](http://nossie.addicts.nl/php5-gd.html)

Works like a charm for me.

---

