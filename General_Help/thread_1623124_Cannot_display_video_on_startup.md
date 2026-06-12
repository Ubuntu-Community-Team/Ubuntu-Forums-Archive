---
title: "Cannot display video on startup"
date: 2010-11-16
forum: General Help
---

### Post by Cremacious on 2010-11-16
I was able to install the newest version of Ubuntu on my laptop with ease, but my not on my home desktop. I installed it inside Windows, and my screen quickly goes to black when I turn the computer on. (This only happens when I boot Ubuntu)
I did a Google search, but I'm new to both Linux and Ubuntu, so things like "grub" doesn't make sense to me. So if anyone can help a beginner like myself figure out how to fix this with easy directions it will be greatly appreciated.

---

### Post by uRock on 2010-11-16
Hello and welcome to ubuntuforums. 

Could you please tell us your system's specs? CPU? Graphics? RAM?

---

### Post by Cremacious on 2010-11-16
hp pavilion a1637c
Windows XP Home Edition SP3
AMD Athlon(tm)64 X2 Dual Core Processor 5200+
1GB RAM
GeForce 6150LE

---

### Post by Cremacious on 2010-11-16
I came across the ability to type in "vga=771", but it doesn't work. Probably cause I'm doing it to the CD.. Well, I looked at this
[https://help.ubuntu.com/community/BootOptions#Change](https://help.ubuntu.com/community/BootOptions#Change) Boot Options Temporarily For An Existing Installation

And it talks about the Grub Boot Menu and editing a kernel. Except... the computer doesn't show that. When I turn on my computer it has me choose between Windows and Ubuntu, but Ubuntu does not display any kernels. It automatically loads and the monitor loses its signal.

---

### Post by dazman19 on 2010-11-16
> **Cremacious said:**
> I came across the ability to type in "vga=771", but it doesn't work. Probably cause I'm doing it to the CD.. Well, I looked at this
[https://help.ubuntu.com/community/BootOptions#Change](https://help.ubuntu.com/community/BootOptions#Change) Boot Options Temporarily For An Existing Installation

And it talks about the Grub Boot Menu and editing a kernel. Except... the computer doesn't show that. When I turn on my computer it has me choose between Windows and Ubuntu, but Ubuntu does not display any kernels. It automatically loads and the monitor loses its signal.

can you get into a terminal? when it boots up do you get a login screen??? 
If not, hold CTRL+ALT and press F2-> F6 and does it give you a terminal?

Log in and see if you can run 

startx

This should load the GUI for you. If not and you get an error let us know what it is and we may be able to help you further..

It sounds like you may need to install a graphics driver, but usually ubuntu is pretty good with common cards like geforce, so it should at least have some basic display lib's.

---

### Post by infektd on 2010-11-16
i have the same problem as well, i had to use nomodset to install. i have a intel internal vid card and an ati in my pci slot which is bad ive heard. i use nomodset in boot edit and i get a gpu freeze so i cant even type startx. ive read making it use the vesa helps, but i cant edit it, i have only one hard drive and a livecd i burned, it wont let me edit any files on the harddrive. help??

---

### Post by Cremacious on 2010-11-16
I can't open a terminal or anything because Ubuntu never actually starts. I pick Ubuntu to start instead of windows and my monitor instantly shuts off.

Instead of something like this where I can press "e" to edit and type in "vga=771" or a similar action...
[http://img163.imageshack.us/img163/8484/grubmenu.png](http://img163.imageshack.us/img163/8484/grubmenu.png)

I get this
[http://img217.imageshack.us/img217/8776/1116002105.jpg](http://img217.imageshack.us/img217/8776/1116002105.jpg)

---

### Post by uRock on 2010-11-16
Did any error messages pop up during the install? 

Did the LiveCD run in the "try without installing" mode?

I am asking because I believe the installer image was bad and/or something went wrong during the install. 

You and I have almost identical on board graphics, so I know that isn't the issue.

---

### Post by Cremacious on 2010-11-17
*Did any error messages pop up during the install? *
Nope

*Did the LiveCD run in the "try without installing" mode?*
Still shuts off monitor

I'm thinking it might be a problem with the video card, so I'm going to replace the video card with a GeForce 6200 dedicated video card and see what happens.

---

### Post by Cremacious on 2010-11-17
By the way, here is a picture of what the screen looks like when it happens.
[http://img219.imageshack.us/img219/1958/1117000706.jpg](http://img219.imageshack.us/img219/1958/1117000706.jpg)

I see it when I try loading Ubuntu at boot and when I try without installing. I used the CD to install in windows, boot/install from CD, and use the Wubi.exe. Each one results in the "No Signal" when trying to boot Ubuntu.

---

### Post by Archeleus on 2010-11-17
All I can think of is that you need to boot straight into the terminal and install the nvidia libraries which for some reason is not there/cannot be found.  When you boot do you get a screen in which you can choose between Windoze and Linux? Select Ubuntu Recovery mode or something like that, and refer to the nvidia website for the terminal installation of the drivers.  After the installation completes you can restart X and it would mostly work.

---

### Post by uRock on 2010-11-17
Can you put the ubuntu LiveCD in, then hit the space bar when the first purple screen comes up, then select the "Check disk for defects" option.

I have the exact same nVidia card, so that shouldn't be giving you any problems.

---

### Post by Cremacious on 2010-11-17
Just got home and changed the video card. It worked!

Thank you all for the responses.

---

