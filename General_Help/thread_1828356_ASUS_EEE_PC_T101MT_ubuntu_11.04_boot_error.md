---
title: "ASUS EEE PC T101MT ubuntu 11.04 boot error"
date: 2011-08-18
forum: General Help
---

### Post by Gippyz on 2011-08-18
I am new to ubuntu or linux.
This is my first ubuntu installation on asus eee pc t101mt.

I installed ubuntu 11.04 using wubi.exe from xp.
Everything went alright, but whenever I boot ubuntu afterwards, error such as this come up :

error : file not found
error : you need to load kernel first.

After press enter it boots to ubuntu no problem.

Any way to fix this? The error is just annoying.

The netbook  is triple boot (win95, winXp, ubuntu).
Kernel : 2.6.38

Thanks in advance guys! :D

---

### Post by Gippyz on 2011-08-18
I am new to ubuntu or linux.
This is my first ubuntu installation on asus eee pc t101mt.

I installed ubuntu 11.04 using wubi.exe from xp.
Everything went alright, but whenever I boot ubuntu afterwards, error such as this come up :

error : file not found
error : you need to load kernel first.

After press enter it boots to ubuntu no problem.

Any way to fix this? The error is just annoying.

The netbook  is triple boot (win95, winXp, ubuntu).
Kernel : 2.6.38

Thanks in advance guys! :grin:
 		                   		  		  		  		  		  	   	 		 
  		 		  	 	 	 	 		  		 			[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG] []("http://ubuntuforums.org/editpost.php?do=editpost&p=11165681")

---

### Post by jfed on 2011-08-18
lol why in all of the universe would you wanna dual boot with NINETY FIVE? hahaha just for the nerd-cred? :p

This doesn't seem like much of a problem haha, in fact I have an ancient desktop from 2000 with mint, and it has the exact same condition. You could just weight down the enter key haha.

Wow I realize this post was not helpful at all, but I just had to comment on that 95 thing xD

---

### Post by Gippyz on 2011-08-19
My bad it isn't 95.
It's dos. It's there to use ghost8 program, save me the hassle of having to rebuild the windows which slow down after couple of months because of stupid collection of temp files they have.

The boot error still exist. Maybe I'll try version 10.10, the most stable one maybe?

---

### Post by dino99 on 2011-08-19
boot on a livecd and install grub:

sudo grub-install /dev/sda

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by cariboo on 2011-08-20
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Gippyz on 2011-08-24
My bad for the double posting.:(
Error is not fixed.
End up installing maverick meerkat.
Works great!:KS
Just find the interface little bit space consuming (left panel).

---

