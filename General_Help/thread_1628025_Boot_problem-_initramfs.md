---
title: "Boot problem- initramfs?"
date: 2010-11-22
forum: General Help
---

### Post by sakura_japan on 2010-11-22
Hello, I'm new member of this community. I've been using ubuntu for about 2 yrs now, but i didn't bother to learn all commands since my computer is up and running, not until recently i have had encountered this problem... 
 
My problem is that I can not boot or login to my computer, it shows these messages:
 
BusyBox v1.13.3 ( Ubuntu 1:1.13.3-1Ubuntu11) built-n shell (ash)
Enter 'help' for a list of built-in commands.
 
(initramfs) 
 
- -end--
 
and the messages goes on and on, honestly i have no idea about the Linux commands... if there is someone who could help me ; i will really appreciate it.
 
by the way the problem got worst when i upgraded from Ubuntu Hardy to 10.10... since then i never got the chance to login again...
 
thank you ,
 
sakura_japan

---

### Post by lmarmisa on 2010-11-22
You will need an Ubuntu Live CD (or pendrive with Ubuntu) in order to fix your computer.

Boot your system from the Live CD, visit this page

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

download the Boot Info Script, run this script and post its output (file RESULTS.txt).

---

### Post by weiersc on 2010-11-28
Hi,

I did not begin this thread, but I have a very similar problem and I am desperate for help.

My system is an AMD Athlone 64x2 Dual core processor.
Ubuntu 10.04 installs perfectly on the system.
But as soon as I do a system update over the internet to 10.10 my problems start. The whole update runs flawlessly, until I have to re-boot.
When it attempts to re-boot into the new kernel, it quickly drops down to a initramfs shell telling me that the /dev/sisk/by-uuid/xxxxxxxxx does not exist.

I have no other option than to reboot using the older kernel from 10.04.

The problem is compounded by the fact that when I try to boot an official 10.10 cd or even the most recent natty CD/DVD - it will not boot. The message that I get then is: Unable to find a medium containing a live file system.

I just came across this thread, and I have now quickly run the Boot Info Script. I attach that here.

I would really appreciate some wisdom and direction.

Thanks, Weiers

---

