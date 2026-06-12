---
title: "Wubi install boots to blank screen, grub boot options needed?"
date: 2010-03-27
forum: General Help
---

### Post by Luke S on 2010-03-27
After going through the windows install dialogs for wubi the computer restarts and from the boot menu I select ubuntu which starts the installer.  The black and white ubuntu logo comes on the screen for a 15 sec or so then goes blank but the harddrive is still active intermittently.  If I wait 5 min or so the computer will restart, at which point I assume it installed the ubuntu.

After the restart and I select ubuntu from the boot menu, ubuntu boots back into the black and white ubuntu logo then the screen goes blank again but this time if I wait it still does nothing with no hard drive activity. If I press "Ctrl+Alt+F1" or "Ctrl+Alt+F2" at the blank  screen it does nothing.  If I reboot and select recovery from the grub boot menu I can boot to a command prompt, if I type "startx" the screen goes blank again.   I though I may need to correct a monitor setting in /etc/X11/xorg.conf but the file does not exist.

Do I need to add a boot option in the grub menu (by pressing e) to fix a hardware or monitor incompatibility? I do not have a clue what options to try or where I need to add them (at the top or bottom of all the commands?)  Any help?

**_Computer setup, custom built:_**
Intel Core i5, socket 1156
ASUS P7P55D, intel P55 express chipset
4Gb Ram, DDR3, 1600Mhz
750gb harddrive with two partitions, ubuntu installed to second partition
nvidia 9500GT
dual LCDs
Windows 7

**_Things I have tried:_**
1) Ubuntu 32 & 64-bit, **same problem**

2) Kubuntu, **same problem**

3) Removing compiz & compiz-core, **same problem**
This idea was suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=984296"), even though the computer is not a Emachine i figured I would try it since he was having the same problem

4) running "sudo dpkg-reconfigure xserver-xorg" command, [B]does nothing: same problem

[/B]5) running "sudo dpkg-reconfigure xorg.conf" command, [B]does  nothing: same problem

6) Just tried Live CD; has the same problem!
[/B]Here is a big clue to the problem. If I hit F4 from the Live CD initial boot prompt and select "Safe graphics mode" I am able to boot the Live CD.

7) Safe graphics mode wubi install, **same problem**
After going through the wubi setup in windows and rebooting I hit ESC directly after selecting ubuntu from the boot menu, I then  select "safe graphics mode".  This does not fix the problem like it does with the Live CD :(

---

### Post by phaed on 2010-03-28
I'm having the same problem, except I don't see the Ubuntu logo.  It goes straight to a blank screen.  But it does the same thing that you described, reading the hard drive for a few minutes, rebooting, then not reading the hard drive.

---

### Post by Luke S on 2010-03-28
TTT.  I edited the post with a few more things I have tried, haven't been able to get anything to work.

---

### Post by Luke S on 2010-03-28
Here is a big clue to the problem. If I hit F4 from the Live CD initial  boot prompt and select "Safe graphics mode" I am able to boot the Live  CD!  Now how do I apply the safe graphics mode to the wubi install?

---

### Post by bluebadger on 2010-05-12
I'm having a similar problem on my Dell 1520 laptop with nv 8400gs graphics card. I'm fairly sure it's some kind of graphics card issue. As soon as I select Ubuntu (also tried with Kubuntu), it tries to complete the installation and gives a short timer. It then goes to a blank screen. Occasionally I get a vertical stripe with some corrupt image partially visible. I'm fairly sure it's not detecting the display properly.

I once got to a point where I actually heard some sort of intro sound. I haven't used Linux in a couple of years... the last time I used Ubuntu I had a bunch of trouble getting sound to work... so from the little I've managed to get it to work at least that has improved but without being able to have basic display detection working... I might just have to stick to Windows for now :(

---

### Post by nowikn on 2010-05-12
Same issue here - was running v9.10 on a HP Pavilion ZE4900 with no issues & attempted a clean install to v10.04 and got the blank-screen-o-death...

Just to be sure I didn't mess up anything, I loaded my XP PRO install disk, wiped any partitions and re-loaded v9.10 with NO ISSUES.

So obviously there is something amiss w/ v10.04

---

### Post by nowikn on 2010-05-18
** BUMP **

Anyone with any input here...?

---

### Post by klutzie on 2010-05-19
I'm getting the same thing from both wubi install and fresh install off cd (and also tried usb flashdisk). 

After selecting 'Install Ubuntu', it reads from the installation media, and then goes into a blank screen.

Running on a Del Inspiron (from about 4 years ago). Will find out model details and graphics card details when I get home.

---

### Post by Mark Phelps on 2010-05-19
You should go to the Installations subforum and read through the pinned thread on Testing Wubi 10.04.  You might find a fix for the problems you're having with Wubi.

---

### Post by nowikn on 2010-05-22
Mark, thanks for the input - however, the point that most of us are trying to make here is this: Ubuntu ran great on v8.x and v9.x using the same hardware setups - however, v10.x cannot install correctly for whatever reason.

The answer that I want to hear from this forum is this: there is an issue that was detected with the v10.x install and will be corrected in the near future.

I love me some Ubuntu but issues like this - simple install issues - frustrate me and many others.  Sorry to vent by I haven't had my first cup of coffee yet this morning . . . 

:mad:

---

### Post by khalidmian on 2010-07-13
Tried installing Ubuntu v 10.04 on laptop with Win7 and Nvidia graphics card. when it reboots I don't see the Ubuntu logo. It goes straight to a blank screen.
Tried the same install on an Xp machine with ATI Card and it works like a charm.
P.S: Used same CD both both installs.
Any clue or feedback would be great

---

### Post by xtremesupremacy3 on 2010-07-13
Sounds to me like you all dont have problems with Wubi, but a glitch I discovered after having installed Ubuntu 10.04. 
If my guess is correct then you are all most likely using a form of NVidia card, but thats only initial observation.

Anyway, have a try at this:

1) Load up your Ubuntu machine, then just after you have passed bios you need to keep the SHIFT button pressed until you are presented with the grub menu.

2)hit e to edit grub settings

3) remove splash and quiet and type in 'nomodeset'

then boot into it.

All being well you should be able to get in, then get the graphics driver through System > Administration > Hardware Drivers.

After a reboot it should work.

That was how I got around it.

---

### Post by skamarla on 2010-07-16
It looks like a video driver issue indeed, but this last advice didn't work for me.

First, you have to boot directly from the CD (get into the BIOS and modify the boot order); then, when selecting install options, get help. One of the items recommends to start with vga=771 when your graphics card is not fully supported. Do that. Get F6, and you get a string with boot options that you can edit. Just add vga=771 and start installation. Everything went fine after that.

---

