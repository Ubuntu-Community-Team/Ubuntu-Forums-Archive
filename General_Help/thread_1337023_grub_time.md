---
title: "grub time?"
date: 2009-11-25
forum: General Help
---

### Post by Rytis on 2009-11-25
Hello,
by default grub takes 10 secs in my pc, but I wanted to decrease this time. I have found howto for grub, and there is this:
> By default you have to press 'ESC' within three seconds. If you want to increase this time limit, you can edit the grub configuration file /boot/grub/**menu.lst**, increasing the seconds in the TIMEOUT part.

But:
```
rytis@troba:/boot/grub$ ls *.lst
command.lst  fs.lst  handler.lst  moddep.lst  partmap.lst  parttool.lst
```

There are no file menu.lst.

Shouls I create it manually? Ot it's hidden somewhere? 
Thanks.

Ubuntu 9.10

---

### Post by wilee-nilee on 2009-11-25
You can install startup manager from synaptic and adjust this time out and the default OS to boot. Grub2 is editable but it is a geeks work.

---

### Post by raktarok on 2009-11-25
Karmic uses Grub2, so you won't find menu.lst. That's for the older versions.  
Look at the link below. While this post is primarily about setting the default boot option, one of the posts explains what to do to reduce the time. You will figure it out..

[http://ubuntuforums.org/showthread.php?t=1336327](http://ubuntuforums.org/showthread.php?t=1336327)

I don't know if startupmanager works with Grub2. I used it in Jaunty,and one time it destroyed my grub configuration. From that time, I lost my faith in the app, but yeah, you can use it if you love GUI. It would certainly be easier than editing files.

---

### Post by spandon on 2009-11-25
Hi Rytis
Startup-Manager does work with Grub2.
you can alter the delay time with it and it is easy to install.
Go to Applications - Ubuntu Software - type Startup in Search box and choose it from the dropdown menu.
Once this is done, you will find it in System - Administration
Don

---

