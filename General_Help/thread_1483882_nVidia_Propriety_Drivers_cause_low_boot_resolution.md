---
title: "nVidia Propriety Drivers cause low boot resolution"
date: 2010-05-15
forum: General Help
---

### Post by TheDarkenedPoet on 2010-05-15
Hey, I have searched all over the internet for a solution to my problem but I have never found one and it is really frustrating me.

Basically when I installed Ubuntu 10.04 on my laptop everything works fine other than extra desktop effects because obviously graphics drivers or not installed yet. All of this is fine and the boot up screen is at my native resolution 1366x768 or something very close and it looks really nice.

The main problem I have is that as soon as I install my graphics driver for nVidia G105m card for some strange reason the boot up screen becomes a very strange resolution and appears to become very glitchy and it is really bugging me.

Instead of the boot screen having a nice purple background and the loading bar and word Ubuntu looking nice and smooth it because large pixelated and every time I boot a big green square flashes during the boot up screen.

This problem goes away as soon as I remove drivers but then obviously I lose desktop effects and then that is just as annoying.

Now my question is, is there anyway way I can either fix my low boot up screen resolution or is there another way in which i can enable desktop effects without installing my drivers?

Any help would much be appreciated.

---

### Post by koolblue3 on 2010-05-15
Hi,

Here is the workaround.

> 
**[COLOR=DarkRed]Bootup/Plymouth.[/COLOR] **
Users should experience a much faster boot however some users may experience problems with Plymouth after the nVidia graphics driver has been enabled. Users may experience plymouth using lower graphics resolution. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/551013]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/551013")

Graphical solution : [http://news.softpedia.com/news/How-t...4-140810.shtml]("http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml")

Command line :
(Some of the fixes put forward dont work for everyone.)
One that works for nVidia and to try is this.
     Code:
     ```
gksu gedit /etc/default/grub
``` and add the line in BOLD.
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
**GRUB_GFXPAYLOAD_LINUX=1680x1050** Save the file and run      Code:
    ```
 sudo update-grub
```The resolution chosen should be your monitors native resolution.
Other graphics card users may get a black screen with flashing cursor  and then a very short duration plymouth. 
[https://bugs.launchpad.net/ubuntu/+s...th/+bug/540801]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801")
One fix for this is to create this file.
```
gksu gedit /etc/initramfs-tools/conf.d/splash
``` 
 and add this option FRAMEBUFFER=y, save the file.
Then
 ```
sudo update-initramfs -u
``` 

Source: [http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

### Post by Ginsu543 on 2010-05-15
You may be experiencing a known bug with Plymouth and nVidia restricted drivers (I had the same problem). There is an easy fix for it. Using Terminal, run:

```

sudo gedit /etc/default/grub

```Go down and locate where it says #GRUB_GFX_MODE=640x480. Right below it, add:

```

GRUB_GFX_MODE=***width***x***height*** (where ***width*** and ***height*** are your native screen resolution)

```Then add this line right below:

```

GRUB_GFXPAYLOAD_LINUX=***width***x***height*** (the same settings as above)

```Save the file. Then, run in Terminal:

```

sudo update-grub

```Reboot and see if your boot-up screen has the correct resolution.

Haha, koolblue3 just beat me to it! :D

---

### Post by jocko on 2010-05-15
The reason is that the nvidia driver is not in use until Xorg starts, so plymouth (the program which among other things display the boot splash) can not use anything else than a low resolution that should work on any graphics cards. The reason that you get a high resolution before you install the nvidia driver is that the open source nouveau driver is capable of kernel modesetting, which allows plymouth to run at your monitors native resolution.

It is possible to set a higher resolution in grub, which will also make plymouth use that resolution. See [this thread]("http://ubuntuforums.org/showthread.php?t=1451820") for more information.

Edit: Oops, I'm typing too slowly.

---

### Post by dentex on 2012-12-14
Since the topic starter didn't, I just wanted to drop a big "THANK YOU" guys for solving this annoying issue.
The solution works perfectly.
 (on Linux Mint 14 cinnamon x86_64 3.5.0-19-generic)

---

