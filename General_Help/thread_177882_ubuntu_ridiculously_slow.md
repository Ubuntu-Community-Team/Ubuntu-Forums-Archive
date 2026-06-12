---
title: "ubuntu ridiculously slow"
date: 2006-05-17
forum: General Help
---

### Post by bayonetblaha on 2006-05-17
I've just installed Ubuntu Hoary on my friend's P4 (128 RAM). I personally watched it start up Windows in a matter of a few seconds and run at a decent speed. I expected better performance from Ubuntu, but it is unreasonably slow. It's taking it about an hour and a half to install 15 packages for the initial update. This just doesn't make any sense... and is certainly giving a bad impression of linux.

It's the sort of slow where clicking on the 'Applications' menu takes 15 seconds.

---

### Post by easyease on 2006-05-17
why hoary?

---

### Post by frodon on 2006-05-17
If your proscessor support hyperthreading, it seems to be the case because you have a P4, you have to know that the default kernel don't support and disable hyperthreading. Therefore if you change your kernel to i686-smp you will improve performances, see this thread for details :
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by Gustav on 2006-05-17
With just 128 mb of RAM you should consider using a lighter desktop enviroment than Gnome (for example XFCE or Openbox).

---

### Post by bayonetblaha on 2006-05-17
frodon, your theory sounds like it's probably right.  As in the tutorial link, I told him to run:

sudo apt-get install linux-686-smp

for a hyperthreaded pentium 2+ proccessor.  I double-checked the ISO that we used to install Ubuntu, it was the 386 version.  If anyone can verify that that would cause such drastic problems, please do. 

I'll have to see how it went in the morning, but I have some concerns about that solution.  I'm pretty sure, now that I think of it, I didn't see the little blue H and T on his processor sticker indicating hyperthreading.  Anyway, the computer was so incredibly slow that it seems it would be something else.  It was taking literally an hour and a half to install those fifteen packages AFTER downloading them.  I can drag a window an inch or so and wait a full minute to see it appear in the new location.  

I suppose if I can get to his computer tomorrow I will try the linux-686 kernel update and a reboot.  If anyone else has ideas, please share them with me! This guy could have a great time with linux if this doesn't make him give up!

---

### Post by bluenova on 2006-05-17
Gnome should be ok, if you use something like the 'Mist' theme, clearlooks and ubuntu human default take a lot of memory. And of cause, use the latest version which is Breezy 5.10

---

### Post by Mustard on 2006-05-17
It does sound like a very strange situation.  Even with 128mb of RAM, it should be running a bit better than that on a P4 machine.  Have you got a swap partition set up?

---

### Post by bayonetblaha on 2006-05-17
Frodon and Mustard thanks a lot, those sound like things that might be wrong.  I've already ruled out the possiblity that these speeds are natural for a P4 128, my laptop is running the exact same thing extremely well on a celeron and 256 RAM.  I'm also not ready to believe that a PC can boot up Windows XP that quickly and then barely run Ubuntu.  There is something else wrong, and I'll try both of those suggestions.

---

