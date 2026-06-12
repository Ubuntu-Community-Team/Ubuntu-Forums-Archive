---
title: "screen resolution on hp nc6220 laptop"
date: 2006-04-05
forum: General Help
---

### Post by icksa on 2006-04-05
Hello:
I recently got an hp 6220 laptop with a 14.1 inch sxga+ screen. I know that the native resolution is 1400x1050, but am unable to set that resolution in gnome. I've been reading online and I know that you have to set the horizontal sync and vertical refresh rates correctly to be able to use the right resolution.

Unfortunately, I cant find the horizontal sync range anywhere. I tried contacting hp, they were no help, I looked in all of the documentation that came with my laptop and tried searching online.

I was wondering if there was anyone out there with this (or a similar) laptop that has managed to get the 1400x1050 resolution working, and if so, could they post what settings they used in their xorg.conf?

Any other suggestions would be really appreciated...

Thanks for your help

---

### Post by karthik085 on 2006-04-05
[http://ubuntuforums.org/showthread.php?t=151451](http://ubuntuforums.org/showthread.php?t=151451)

---

### Post by icksa on 2006-04-05
Hi:
I know you can set the resolutions directly in the xorg.conf file in the screen section. But I think that if you have the wrong horizontal sync/vertical refresh rates X will refuse to display that resolution, and will look for one that will work, which in my case is 1280x1024...

---

### Post by karthik085 on 2006-04-05
just reconfigure xserver. so, you don't need to manually edit the xorg.conf file.

---

### Post by icksa on 2006-04-05
Hi:

sudo dpkg xserver-xorg
Produced the response "dpkg: need an option"

so I tried:
sudo dpkg --configure xserver-xorg
which produced "package xserver-xorg is alread installed and configured"

---

### Post by icksa on 2006-04-05
Hi:
I figured out what to do...

First you need to apt-get 855resolution

Then run:
sudo 855resolution -l
This lists the available resolutions for your monitor, then you need to overwrite one of them with 1400x1050, for example:

sudo 855resolution 3c 1400 1050

Finally, you need to run this script (sudo 855resolution) every time your computer starts, before X loads, and you should be able to use all of the available resolutions...

My last question is...what is the correct way to get this script to run when the computer boots, before x loads? In gentoo I did:
rc-update add 855resolution default

What is the equivalent command for ubuntu?

Thanks

---

### Post by princeton on 2006-04-05
I made a script for Dapper to do that.  I never got any feedback whether it worked or not, but you might try it for Breezy.  See this thread:

[http://ubuntuforums.org/showthread.php?t=144177&highlight=855resolution](http://ubuntuforums.org/showthread.php?t=144177&highlight=855resolution)

Let me know if it works or not.

---

