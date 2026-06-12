---
title: "please help me ati drivers 8.8.25"
date: 2005-01-24
forum: General Help
---

### Post by mud on 2005-01-24
I have tried everything to install ati drivers. now new ones are out! 8.8.25.please someone help me ive been working on this for months! 
I have ubuntu warty w/ kernel 2.6.8.1  XFree86 4.3
I am starting from a fresh ubuntu install.
as i understand it u have to recompile the kernel and then install ati drivers.
I de-selected ati radeon and all other drm support in kernel with make menuconfig.
I was able to compile kernel.
i booted with the new kernel and it worked fine.
when i installed ati driver and restarted the x server would not start.
I used instructions from wiki to recompile kernel and did the stuff on the ati driver page.
[http://www.ubuntulinux.org/wiki/KernelByHandHowto](http://www.ubuntulinux.org/wiki/KernelByHandHowto)
[http://www.ubuntuforums.org/showthread.php?t=3567&highlight=ati+drivers](http://www.ubuntuforums.org/showthread.php?t=3567&highlight=ati+drivers)
i used the defaults in fglrxconfig except : use external agpgart "y"
help me please so i dont have to go back to windows!  :cry: 
Im an enemy territory addict who just wants to play but ive been spending all of my time with ati drivers.

---

### Post by poofyhairguy on 2005-01-24
[QUOTE=mud]I have tried everything to install ati drivers. now new ones are out! 8.8.25.please someone help me ive been working on this for months! 
I have ubuntu warty w/ kernel 2.6.8.1  XFree86 4.3
I am starting from a fresh ubuntu install.
as i understand it u have to recompile the kernel and then install ati drivers.
I de-selected ati radeon and all other drm support in kernel with make menuconfig.
I was able to compile kernel.
i booted with the new kernel and it worked fine.
when i installed ati driver and restarted the x server would not start.
I used instructions from wiki to recompile kernel and did the stuff on the ati driver page.
[http://www.ubuntulinux.org/wiki/KernelByHandHowto](http://www.ubuntulinux.org/wiki/KernelByHandHowto)
[http://www.ubuntuforums.org/showthread.php?t=3567&highlight=ati+drivers](http://www.ubuntuforums.org/showthread.php?t=3567&highlight=ati+drivers)
i used the defaults in fglrxconfig except : use external agpgart "y"
help me please so i dont have to go back to windows!  :cry: 
Im an enemy territory addict who just wants to play but ive been spending all of my time with ati drivers.[/QUOTE]


Hmmm....Hoary had the newer ati drivers added recently. Warty might have them- add "restricted" next to main in synaptic.

In all honesty getting the official drivers working might not matter. I have an ATI card that I got the drivers working for- but the 3d performance is piss-poor.

Its not Linux's fault, its ATIs! For not releasing good drivers. My girlfriends laptop hardware (half my mhz, geforce 420 go VS. 9600 pro) is much better for 3d games in Linux than mine is.

I dual boot to play games. Its not bad- when I'm in Linux I actually do work on the computer.

---

### Post by jensyt on 2005-01-24
I had problems with the older drivers for about a week before getting them to work, but I did eventually figure that out. I was lucky enough to be running Hoary for the newer drivers, and they simply worked (after a day of tinkering).

To help you at all, first, did you read the information about it on ATI's website? They have some relatively useless instructions on how to manually install everything, but it helped me a little bit. What I had to do with the old drivers, assuming the new ones install the same way, was convert them to .deb with alien, then dpkg --force-overwrite -i whatever-package.deb

After that, I had to manually make and install the kernel module (make sure you have the right source linked to /usr/src/linux). This link explains what I had to do for that: [http://ati.com/support/infobase/4484.html](http://ati.com/support/infobase/4484.html)

But before doing all of that, I'd like to say that I don't suggest this route. Sure, it got my hardware acceleration working nicely so I could play Enemy Territory again, but it wasn't too bright. I'm fairly lucky I didn't mess anything up, so you've been warned.

Also, on another side note, this is assuming you're so desperate that you want to install them manually, instead of via the repositories.

---

### Post by mud on 2005-01-24
well i got ati drivers to work in knoppix.
it would only work if i used a different kernel than the one knoppix came with.
it had 2.6.9 so i installed 2.6.8.1 and it worked.2.6.10 also worked with a patch.
ill try the same for ubuntu and see if it works.

---

### Post by telmo on 2005-01-25
[QUOTE=mud]I have tried everything to install ati drivers. now new ones are out! 8.8.25.please someone help me ive been working on this for months! 
I have ubuntu warty w/ kernel 2.6.8.1  XFree86 4.3
I am starting from a fresh ubuntu install.
as i understand it u have to recompile the kernel and then install ati drivers.
I de-selected ati radeon and all other drm support in kernel with make menuconfig.
I was able to compile kernel.
i booted with the new kernel and it worked fine.
when i installed ati driver and restarted the x server would not start.
I used instructions from wiki to recompile kernel and did the stuff on the ati driver page.
[http://www.ubuntulinux.org/wiki/KernelByHandHowto](http://www.ubuntulinux.org/wiki/KernelByHandHowto)
[http://www.ubuntuforums.org/showthread.php?t=3567&highlight=ati+drivers](http://www.ubuntuforums.org/showthread.php?t=3567&highlight=ati+drivers)
i used the defaults in fglrxconfig except : use external agpgart "y"
help me please so i dont have to go back to windows!  :cry: 
Im an enemy territory addict who just wants to play but ive been spending all of my time with ati drivers.[/QUOTE]

Please tell me if you get it to work. I sure would like to have that sooooo needed 3D aceleration!

THX

---

### Post by Mark Hobley on 2005-02-18
Hi.

If you are using an ATI Radeon 9000 or below, Enemy Territory will work fine with the open source drivers provided with the 2.6.x kernel.

Do not download drivers from the ATI website, since you will taint your kernel.

I recommend that you use Debian Testing (Sarge) with a 2.6.x kernel.

I play Enemy Territory on Linux :)

Regards,

Mark.

--

Mark Hobley
393 Quinton Road West
QUINTON
Birmingham
B32 1QE

Telephone: (0121) 247 1596
Email: markhobley at hotpop dot donottypethisbit com

[http://markhobley.yi.org/](http://markhobley.yi.org/)

---

### Post by bobmitch on 2005-02-19
See my rough-and-ready howto in this thread for installing the new ati drivers:

[ATI Howto](http://ubuntuforums.org/showthread.php?t=15990) 

Yes, a package would be nice, but if you want cutting edge, this is the way to do it.

---

### Post by mud205 on 2005-02-25
I finally got it working and i must say better than ever!!getting 1988fps glxgears radeon 9600.Thanks to Bobmitch and others for their howto's could not have done it without y'all.so here is exactly what I did.
First of all Ubuntu Hoary.AMD 2500+ 
added community maintained and non-free hoary repositories
installed build-essential, glibc2.2, linux-headers 2.6.10-3-386, and linux-restricted-modules 2.6.10-3-386.
downloaded latest fglrx (8.10.19)
then I ran these commands in this order.
Disclaimer:I am no linux expert i dont even know what some of these commands do I just pieced together this information from these forums and got my 3D working.I am posting this because it worked for me. if it needs improvement or u notice an obvious typo email me at:de2005@comcast.net
1. sudo /etc/init.d/gdm stop
2. sudo mv /lib/modules/<kernel version here mine is 2.6.10-3-386>/kernel/drivers/video/fglrx.ko /home/<your home folder>/
3. sudo alien fglrx........rpm
4. sudo dpkg --force-overwrite fglrx..........deb
5. cd /lib/modules/fglrx/build_mod
6. sudo sh make.sh
7. cd ..
8. sudo sh make_install.sh
9. sudo fglrxconfig
10. sudo modprobe fglrx *IMPORTANT note if u dont use sudo here u will get : fatal : error inserting fglrx (/lib/modules/2.6.10-3-386/kernel/drivers/char/drm/fglrx.ko)
11. sudo /etc/init.d/gdm start
12. restart
13. whew!
14. fglrxinfo
14.if it says ati radeon celebrate with a game of enemy territory  :D

---

