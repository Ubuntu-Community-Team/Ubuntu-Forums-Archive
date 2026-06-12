---
title: "Startup Manager Issues"
date: 2011-07-05
forum: General Help
---

### Post by age99 on 2011-07-05
Hi, I recently upgraded to 11.04, but I am having trouble configuring grub.  I used to use the Startup Manager, but now if I modify anything with Startup Manager it doesn't change the booting whatsoever.  

I am running a Win7 Dual Boot, but I can't change the default or the timing or any of the other options.

Any ideas what I can do? Is there a manual way to do this?

Thanks

---

### Post by raja.genupula on 2011-07-05
sudo gedit /boot/grub/grub.cfg



make a look at that file, it will open a grub file . there you can change the grub  time and all .

---

### Post by wildmanne39 on 2011-07-05
Hi, have a look at this link and also install grub 2 customizer.
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

### Post by Mark Phelps on 2011-07-05
> sudo gedit /boot/grub/grub.cfg

Do NOT do this -- repeat, NOT do this!

There's a reason this file says to NOT edit it -- because it gets regenerated automatically when you do updates.

The files you edit are located in /etc/grub.d.

---

### Post by age99 on 2011-07-05
I tried to install the customizer, but modifying it has no affect, similar to the Startup Manager.  Any idea why this is?
Is it normal for Startup Manager not to work?  If so, why does it exist?

In past versions, I modified the grub.cfg file, however I would like to find a better way to do it.  Is there a straightforward way to do this?

Thanks

---

### Post by age99 on 2011-07-13
Ok, so I got it work work, sortof.  It seems that many of the options listed on the Startup Manager were not present on the actual menu.  So by playing around with the "default" I manged to figure out which deault I wanted.

Still seems like a mess, but I got it working.

---

### Post by blackheartnaz on 2011-07-13
this is similar to my problem regarding startup manager.
i have recently updated my Ubuntu Linux 10, and to my surprise, more options to boot from appeared on my Startup Menu. 

i hope i can get by with this guide...:KS

---

