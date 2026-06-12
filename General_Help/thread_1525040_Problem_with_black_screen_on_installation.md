---
title: "Problem with black screen on installation"
date: 2010-07-06
forum: General Help
---

### Post by alfredhitzkopf on 2010-07-06
I just tried to install ubuntu. after the cd didnt work because of "user id not valid"-problem i finally got the usb stick to boot. but now i have a new problem. after i hit install everything seems to start off ok but then suddenly i get a black screen and nothing happens anymore. does anyone have any ideas. i would be really thankful because im starting to greak out completely :)

---

### Post by dino99 on 2010-07-06
mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by lordskid on 2010-07-06
I experienced that too. But I waited it out. and everything went okay. it was an approximately 10 minutes wait. I was using an acer tm 3210 laptop.

---

### Post by alfredhitzkopf on 2010-07-06
even 20 minutes didnt help. ill try installing 9.10 now and then uptdate. hopefully that will work

---

### Post by alfredhitzkopf on 2010-07-06
ok 9.10 works. sadly after the update i get a black screen on startup again. any ideas?

---

### Post by Rubi1200 on 2010-07-06
Hi,
please post your computer specs. here; RAM, computer make, other operating systems, and, most importantly, graphics card.

Also see here:

[http://ubuntuforums.org/showpost.php?p=9543761&postcount=2](http://ubuntuforums.org/showpost.php?p=9543761&postcount=2)

Look at the workarounds mentioned towards the bottom of the post.

Oh, last but not least welcome. :)

---

### Post by alfredhitzkopf on 2010-07-06
ok i got it now. the problem is the intel 855GME chipset. heres what i did

1.insert the installation disk

2. hit F6 and add the following to the command line
> i915.modeset=0 xforcevesa

3. Install Ubuntu and restart

4. Log in and create a simple textfile with following content using gedit-Editor

> Section "Monitor"
Identifier "VGA"
Option "Ignore" "true"
EndSection

5. save it somewhere for example in your home-folder

6. copy it in your /etc/X11-folder using the terminal with

> sudo cp /home/ /etc/X11

I hope this will help people with the same problem

---

