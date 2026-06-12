---
title: "No splash screen"
date: 2010-06-01
forum: General Help
---

### Post by fran9 on 2010-06-01
Hey guys, could you please help me with the problem. I installed 10.04 on my Toshiba laptop, but for some reason there is no violet splash screen with the "Ubuntu" word when the system is loading. Instead there is a bald dash in the upper left corner that keeps blinking and then it is changed by regular font dash, then there are some letters (like system is checking something?) and that's it, one second after my desktop welcomes me. What could be the problem? I feel like I haven't had such a problem when I was installing it on another computer. Though it might be because I am installing from USB drive, but not, installed from CD with the image recorded and still the same problem. :confused: Please help, it doesn't bother me really, but just trying to figure out why. Thank you.

---

### Post by emptybox on 2010-06-01
You might find the solution here.

[http://ubuntuforums.org/showthread.php?t=1469475]("http://ubuntuforums.org/showthread.php?t=1469475")

Perhaps
[quote=Philinux]...Other graphics card users including nVidia may get a black screen with flashing cursor and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801](https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801)
One fix for this is to create this file.

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option FRAMEBUFFER=y, save the file.
Then

```
sudo update-initramfs -u
```
[/quote]

It worked for me with a similar problem anyway. :)

---

### Post by fran9 on 2010-06-01
Thank you, it worked :)

---

