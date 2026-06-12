---
title: "Totally new user..."
date: 2009-07-19
forum: General Help
---

### Post by zozie on 2009-07-19
Hallo all;

Just installed Ubuntu on my Dell Inspiron 1318. The installation was smooth and everything works fine including the WIFI. (Not Intel)
2 issues. When I open the lid, or start the machine, it takes a minute or so to connect to the previous wifi connection which is a bit annoying. Is there a way to speed that up?

The other thing, sometimes it seems to be running very slow. The HDD light is flashing crazy and take a long time open anything.... Haven't been able to figure out what causes it cause when I check the performance, it's not even using the swap file.
My config: Intel core 2 Duo @ 2.66 GHZ 4GB ram with cheapy Intel VGA card, 320 GB 7200 RPM Hdd.

Main issue. I installed Linux here cause I need to migrate a simple C program that sends some data to the serial port for a robotics application. Anyone know what USB to serial adaptor I can use with Ubuntu? I have a couple different ones but I don't even know how to check what ports I have installed.... Would appreciate some help there. Something similar to Vindoz' device manager?

Thanx. 

BTW. Last time I played with linux was 4 years ago with another distro and I gotta say I'm VERY surprised how far things have gone. Everything's so smooth.:D

---

### Post by philcamlin on 2009-07-19
are you using wubi?

wubi was always slow for me because its on a virtual file system

---

### Post by Shpongle on 2009-07-19
to speed up your system have a look at this [http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast](http://tuxtraining.com/2008/09/28/how-to-make-ubuntu-extremely-fast), i only used prelink preload and tuned the swappiness, and i noticed an increase in speed,

be careful though, if your unsure ask here and also read the comments below the article

---

### Post by zozie on 2009-07-19
Thanx I'll look at that.

---

### Post by t4thfavor on 2009-07-19
Your Serial to USB adaptor will be in port ttyUSBX where X is usually 0, but could be something different. Most serial to USB adaptors will work, though I have a belkin that does not work.

Good luck with the C program, I always like to see people porting software away from windows platforms, especially when its for some kind of embedded device.

---

### Post by mikewhatever on 2009-07-19
Hardinfo from the repositories is somewhat similar to the device manager in Windows.

---

### Post by zozie on 2009-07-19
I installed hard info but it's not showing up in the menu:(. I'll try installing it again

---

