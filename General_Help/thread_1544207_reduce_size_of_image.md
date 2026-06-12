---
title: "reduce size of image"
date: 2010-08-01
forum: General Help
---

### Post by prakhar_garg009 on 2010-08-01
hiii frends
i m using ubuntu 10.4 version and i want to knw that is their any software or something else so that i can resize my images from 2 mb to in kb

as my image folder is of 614 mb and i want to put that folder images in my mobile so how can i reduce the size of that folder

---

### Post by amite on 2010-08-01
install imagemagick :
$ sudo apt-get install imagemagick
$ man imagemagick

use mogrify
or 
gui tool of imagemagick
$ display

---

### Post by Smart Viking on 2010-08-01
Hey, there is a command line tool which could be useful which is called "convert", it can work with images.

If i was you i would make all the images smaller, that you can do with this command:

```
convert -resize 100x40 input.jpg output.jpg
```where the "100x40" means how many pixels the image will be when it is done converting, you should pick something that will look good, dont just take a random height and width, and you can do this with almost all image types, not only jpg, what you will need to do is to use some wildcards on the input and output files so that it will match all images(i think that would work). Anyway i hope this helps and good luck. :)

---

### Post by agnes on 2010-08-01
You could also convert quality without resizing ```
for i in `ls`; do convert -quality 50 $i new-$i; done

```

---

### Post by prakhar_garg009 on 2010-08-02
hiii frends
is their any software in ubuntu 10.4 by which we reduce the size of images i.e., from 2mb to 150 kb or smthin else

---

### Post by Smart Viking on 2010-08-02
Hello, you must not create duplicate threads, continue in the thread you made yesterday.

[http://ubuntuforums.org/showthread.php?t=1543591](http://ubuntuforums.org/showthread.php?t=1543591)

---

### Post by TopEnder on 2010-08-02
> **prakhar_garg009 said:**
> hiii frends
is their any software in ubuntu 10.4 by which we reduce the size of images i.e., from 2mb to 150 kb or smthin else
This package "[COLOR="Blue"]nautilus-image-converter[/COLOR]" in Synaptic Package Manager that maybe what you are looking for.

---

### Post by prakhar_garg009 on 2010-08-02
after installing it from synaptic where it will be found

---

### Post by philinux on 2010-08-02
Threads merged. Don't create multiple threads for same problem thanks.

Try using the Gimp from Apps > Graphics

Or install gthumb. It's a bit simpler to use.

---

