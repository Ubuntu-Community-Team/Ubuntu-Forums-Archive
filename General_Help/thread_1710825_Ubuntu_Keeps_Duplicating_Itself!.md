---
title: "Ubuntu Keeps Duplicating Itself!"
date: 2011-03-20
forum: General Help
---

### Post by khoraski on 2011-03-20
After I got Ubuntu, when I boot my PC, the boot menu has a list of OS's I can boot it. 

It said like:

[LIST]
Ubuntu 10.04 LTS
Ubuntu (safemode)
Windows Driver Test
Windows Vista
Windows 7
[/LIST]
It always worked just fine if I selected Ubuntu 10.04 LTS. But then later, a few days later, I booted my PC and it said:

[LIST]
Ubuntu 10.04 LTS
Ubuntu (safemode)
Ubuntu 10.04 LTS
Ubuntu (safemode)
Windows Driver Test
Windows Vista
Windows 7
[/LIST]

See? There are two of each. I just decided to ingore it, but now it's saying:

[LIST]
Ubuntu 10.04 LTS
Ubuntu (safemode)
Ubuntu 10.04 LTS
Ubuntu (safemode)
Ubuntu 10.04 LTS
Ubuntu (safemode)
Windows Driver Test
Windows Vista
Windows 7
[/LIST]

There are SIX DARN UBUNTU THINGS!

WHAT DO I DO?!

---

### Post by TeoBigusGeekus on 2011-03-20
[http://ubuntuforums.org/showthread.php?t=1695877]("http://ubuntuforums.org/showthread.php?t=1695877")

---

### Post by Rubi1200 on 2011-03-20
If you have been keeping the machine updated on a regular basis, then these are probably older kernels. GRUB stores them in the menu so you can boot to an older version for troubleshooting purposes if needs be.

Post the contents of the following file please:

> /boot/grub/grub.cfg 

This will confirm what is on the menu.

---

### Post by khoraski on 2011-03-20
> **TeoBigusGeekus said:**
> [http://ubuntuforums.org/showthread.php?t=1695877]("http://ubuntuforums.org/showthread.php?t=1695877")

When I search "linux-image" I get no results.

---

### Post by TeoBigusGeekus on 2011-03-20
Scroll down a bit through the results.

---

### Post by khoraski on 2011-03-20
> **TeoBigusGeekus said:**
> Scroll down a bit through the results.

I don't get it. what do I do next when I find Linux-image?

---

### Post by TeoBigusGeekus on 2011-03-20
What are the versions of the linux images you have installed?
Post them all, or post a screenshot.

---

### Post by khoraski on 2011-03-20
> **TeoBigusGeekus said:**
> What are the versions of the linux images you have installed?
Post them all, or post a screenshot.

Wait, never mind. I just uninstalled the two green selected things with a lower number than the third. And it worked. 

Thanks. :D

---

### Post by TeoBigusGeekus on 2011-03-20
Just bear in mind that it's a good idea to keep the last two kernels for safety reasons: if the latest one fails you, you can revert to the previous one.

---

### Post by Timmer1240 on 2011-03-20
To remove all the unused Linux Kernel headers, images and modules, simply run this command: dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge

---

