---
title: "CHmod and file permissions"
date: 2010-12-10
forum: General Help
---

### Post by Jragon on 2010-12-10
Hello,

I'm very new to ubuntu, and I am a developer in web. I have installed php, mysql, and apatche. And i need the /var/www/ folder to be able to be read witten, and acsessed by anything. I have tried chmodding 777. But it still doesnt work.

Thanks

Jragooon

---

### Post by Verbeck on 2010-12-10
remember to use recursive
```

sudo chmod 777 **-R** /var/www

```

---

### Post by Jragon on 2010-12-10
Thanks. There seems to be something still wrong with it though... This is my code:

[PHP]<?php
error_reporting(E_ALL);
 /*for($i = 1;$i <= 9;$i++){

  // an email address in a string
  $string = "$i";

  // some variables to set
  $font  = 4;
  $width  = ImageFontWidth($font) * strlen($string);
  $height = ImageFontHeight($font);
  $path = "/var/www/randoms/count/$i.jpg";
  // lets begin by creating an image
  $im = @imagecreatetruecolor ($width,$height);

  //white background
  $background_color = imagecolorallocate ($im, 255, 255, 255);

  //black text
  $text_color = imagecolorallocate ($im, 0, 0, 0);

  // put it all together
  imagestring ($im, $font, 0, 0,  $string, $text_color);

  // and display
  imagejpeg ($im, $path);

 }
 echo 'sucsees';*/
 // Create a blank image and add some text

$im = imagecreatetruecolor(120, 20);
$text_color = imagecolorallocate($im, 233, 14, 91);
imagestring($im, 1, 5, 5,  'A Simple Text String', $text_color);

// Save the image as 'simpletext.jpg'
imagejpeg($im, 'simpletext.jpg');

// Free up memory
imagedestroy($im);
echo "worked";
?>[/PHP]

The bit after the comment is from php.net so it should work =S

---

### Post by Krytarik on 2010-12-10
I suggest using a different parent-dir than "var" for the "www"-dir, if it's possible.
Because apparently you *may* have to also make the parent-dir accessable/writeable for everyone. I had a similar problem with a custom installation of "Vuze" (for which I've chosen /opt as parent-dir).

---

### Post by Jragon on 2010-12-10
That made no sense to me.

---

### Post by Krytarik on 2010-12-10
> **Jragon said:**
> That made no sense to me.
For me neither.;)

---

