---
title: "how can I change the grub picture in Ubuntu 11.10"
date: 2011-11-01
forum: General Help
---

### Post by Lukasz Tarkowski on 2011-11-01
how can I change the grub picture in Ubuntu 11.10

---

### Post by pqwoerituytrueiwoq on 2011-11-01
google grub customizer ppa
it may have the option (i would look but i am using grub legacy)

---

### Post by Vaphell on 2011-11-01
[http://ubuntuforums.org/showthread.php?t=1739412](http://ubuntuforums.org/showthread.php?t=1739412)

> Copy any image (jpg, png or tga) to the /boot/grub folder.
Run "sudo update-grub".

---

### Post by sammiev on 2011-11-01
> **Vaphell said:**
> [http://ubuntuforums.org/showthread.php?t=1739412](http://ubuntuforums.org/showthread.php?t=1739412)

Use it on all my computers and can only add +1 :) Very easy to change your grub picture and shorten your boot time. :)

---

### Post by oldfred on 2011-11-01
Also:

Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

### Post by Lukasz Tarkowski on 2011-11-05
I have tried everything and disabling the save_default and background of grub2 still won't change,  I also tried the super boot grub and grub customizer nothing wokred.

---

### Post by sammiev on 2011-11-05
> **Lukasz Tarkowski said:**
> I have tried everything and disabling the save_default and background of grub2 still won't change,  I also tried the super boot grub and grub customizer nothing wokred.

With grub customizer you must save it after you change it or when you quit the changes will not be saved. :)

---

### Post by Lukasz Tarkowski on 2011-11-05
I did that, still won't work,  I think there is a bug

---

### Post by Cpierce on 2011-11-05
Try it again with grub customizer , but before you do, make sure the picture you are trying to use is in .png extension. Jpeg pictures are hit and miss. I use gimp to open the jpegs and then save them in .png

---

### Post by batharoy on 2011-11-05
> **Vaphell said:**
> [http://ubuntuforums.org/showthread.php?t=1739412](http://ubuntuforums.org/showthread.php?t=1739412)> Copy any image (jpg, png or tga) to the /boot/grub folder.
Run "sudo update-grub".

This worked for me but I had to remove the existing .png in the grub folder first.

---

### Post by drs305 on 2011-11-05
I agree with *Cpierce* about using png images.

We can work backward if you like. The final product of the Grub 2 scripts is /boot/grub/grub.cfg

The line which incorporates the image, if it resides in /boot/grub and you don't use a theme, is in the 05_debian_theme section. For my image, it looks like this and appears around line 70:
> if background_image /boot/grub/**drs305.png**; then
  true
else

Do you have this line and is the image path and name correct? 

If so, try using the attached image by placing it in /boot/grub and changing your grub.cfg to look like the above. Do NOT update Grub. Reboot and see if a known, working png image works for you.

---

### Post by Lukasz Tarkowski on 2011-11-13
The Image has to be the same as your resolution of Graphic card in for it to work.  Copying using sudo cp to etc/grub has worked perfectly, just remember to resize it, also the grub-customizer works now :)

---

