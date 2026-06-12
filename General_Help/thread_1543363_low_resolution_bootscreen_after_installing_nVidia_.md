---
title: "low resolution bootscreen after installing nVidia driver"
date: 2010-08-01
forum: General Help
---

### Post by gufide on 2010-08-01
Just in the title, and my native resolution is 1366x768

---

### Post by Raymond2201 on 2010-08-01
Hey, alot of people are having the same issues with proprietary drivers for both Nvidia and ATI and sadly to my knowledge there is no official fix for it, there are hacks to get it to work

[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

Sadly the other methods are either live with it or revert to open source drivers.

---

### Post by 23dornot23d on 2010-08-01
The way I do it below is similar to the above ...

Boot loader problem .. [setting the boot menu]("http://ubuntuforums.org/showthread.php?t=1296225") ..

If its the overall resolution and the graphics acceleration is borked - the solution is in my footer

The way I solve it is in my signature ,,,, Nvidia Solution ,,,, 
__________________________________________________

I used it today and it worked ..... but make sure to get the top line ..... its in grey

$ sudo aptitude install build-essential linux-headers-`[COLOR=Red]uname -r[/COLOR]'

It ensures the headers are there for your kernel build ....

I did this part in a console window to get the kernel version

[COLOR=Red]uname -r
[/COLOR] 
and then cut and pasted the result onto the end .......
for some reason the line failed to work as it should do ....

---

### Post by Raymond2201 on 2010-08-01
> **23dornot23d said:**
> The way I solve it is in my signature ,,,, Nvidia Solution ,,,, 
__________________________________________________

I used it today and it worked ..... but make sure to get the top line ..... its in grey

$ sudo aptitude install build-essential linux-headers-`[COLOR=Red]uname -r[/COLOR]'

It ensures the headers are there for your kernel build ....

I did this part in a console window to get the kernel version

[COLOR=Red]uname -r
[/COLOR] 
and then cut and pasted the result onto the end .......
for some reason the line failed to work as it should do ......

ATI slacking for a decent workaround! 
<--- has ATI card hehe

---

### Post by 23dornot23d on 2010-08-01
Strange thing is that the Mint version of GRUB2 .... seems to be working great.

Why Ubuntu do not have the same one is beyond me ..... one day it will all standardize

Then they will bring out GRUB3 ....... ;)

---

### Post by Raymond2201 on 2010-08-01
I think Mint package all the proprietary stuff in their distro so it's all tested before it ships out, Ubuntu have to meet their release schedule as a result some things might not get tested fully.

gives me something to complain about i guess =D>

---

### Post by 23dornot23d on 2010-08-01
I tried to work out what was happening with the Boot Menu and the rest of it ....
seems we have [work around's]("http://sites.google.com/site/linuxbootubuntu/") though so thats good.

---

### Post by gufide on 2010-08-01
sorry, I get only a BAD resolution, so bad that the loading image writes "lubuntu" just fit on my screen but is not so ugly xD

---

### Post by fuzetsu490 on 2010-08-01
The fix for this is in the sticky in this section ([http://ubuntuforums.org/showthread.php?t=1469475]("http://ubuntuforums.org/showthread.php?t=1469475")) under "Bootup/Plymouth" i had the same problem but now its more or less fixed.

---

