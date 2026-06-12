---
title: "Plymouth problems"
date: 2010-11-20
forum: General Help
---

### Post by Dans564 on 2010-11-20
Hey every1.  From searching the internet I have figured Plymouth problems are pretty common, with tons of different fixes.  My hope is some1 knows a fix for my problem :D.

Ok so here it goes...
I have 2 Nvidia GTX 460's and I'm using the non-free driver.
I'm on Linux Mint 10 64bit. (mint people can post here right???)
When i boot i get a black screen with huge, ugly, pixelated letters and dots. Very ugly!
I did some searching and came across "Plymouth Manager" on OMGubuntu blog.  The app can change boot resolution, and also has a tab to get plymouth to play nice with non-free drivers.  I ran the non-free script provided, set the resolution to my screens reso (1920x1080 or 1080p) and was feeling very luck.  Restarted, and to my dismay, still was greeted with big ugly letters and dots.  

If any1 has any advice on how to get a pretty boot screen, i would mega appreciate it.  I'm pulling my hair out on this lol.

---

### Post by Dans564 on 2010-11-20
I have been searching for hours and haven't found anything.  Maybe I should just get used to an ugly boot...

---

### Post by Frogs Hair on 2010-11-20
Take a look here. [http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

---

### Post by Dans564 on 2010-11-20
thanks for the suggestion.  As it turns out that is the same script that is included the app "plymouth Manager" app that i mentioned in my first post.  so the result is the same... big ugly dots and letters:-({|=
thanks again though

---

### Post by Frogs Hair on 2010-11-20
There is a fix for 10.04  , but I have been unable to find a 10.10 compatible version of the instructions and it looks like a lot of work .

---

### Post by Dans564 on 2010-11-20
Thanks for looking I really appreciate it.  Whats the name of the 10.04 fix?  just wondering.

---

### Post by Frogs Hair on 2010-11-20
> **Dans564 said:**
> Thanks for looking I really appreciate it.  Whats the name of the 10.04 fix?  just wondering.

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by Dans564 on 2010-11-21
hey I'm trying out that link for 10.04 even though I'm on 10.10.  This is cause I'm desperate and I don't remember much changing in the boot process for 10.10, so I'm guessing it will work.

Every command in the tut goes of without a hitch until the very last one:

```
sudo update-initramfs -u
```

and i get this in return:

```
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Warning: No support for locale: en_US.utf8

```

I have a feeling that warning has something to do with my ugly boot.  en_US.utf8 is language file I think?  Does anyone have any thoughts on this??

thanks again

---

### Post by Dans564 on 2010-11-21
No more big ugly dots!  But still no Plymouth :( . its now is "Linux mint" with 4 dots small and up in the left hand corner of the screen.  This is progress, but still not fixed.  The resolution that the boot is set at is 1280x1024-24 because this is the highest that "Plymouth manager" says my gpu is capable of.  Although, when totally up and running my desktop resolution is 1920x1080 or 1080p.  I'm supper confused and frustrated at this point.  All i want is an attractive boot screen!  Also, on shutdown plymouth works.  My selected theme is shown and is clear and un-pixelated, but has about a 2 inch black border around it.  Im confused.......

---

### Post by Krytarik on 2011-01-08
Have you managed to fix it meanwhile?

This is an excerpt from the Plymouth readme, try the Framebuffer option first:
> High-color graphics on nVidia, ATI and other cards
--------------------------------------------------

Our default configuration uses low-color graphics on cards or drivers
for which "Kernel Mode Setting" (in-kernel graphics drivers) are not
available.

This is because the driver that permits high-color graphics tends to
cause issues with suspend and resume, and we opted to prefer that
working.

    For nVidia and ATI users, the default "nouveau" and "radeon"
    drivers are Kernel Mode Setting enabled, but do not always
    provide 3D capability at the current time.  By switching to
    using the restricted/non-free nvidia-glx or fglrx drivers,
    you will gain 3D capability at the loss of a high-color
    splash screen.

You can however chose to enable high-color (and resolution) console
if you find it doesn't affect suspend/resume for you, or you don't
use that feature.

There are various methods of doing this, the most robust is the
following four steps:

 Append video=vesafb to the GRUB_CMDLINE_LINUX_DEFAULT in
   /etc/default/grub
 sudo update-grub

 echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash
 sudo update-initramfs -u

---

