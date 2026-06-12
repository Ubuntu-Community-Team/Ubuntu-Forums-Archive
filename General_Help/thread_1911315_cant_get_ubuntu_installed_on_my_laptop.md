---
title: "cant get ubuntu installed on my laptop"
date: 2012-01-18
forum: General Help
---

### Post by jbunch on 2012-01-18
I have tried just about everything I can think of to get Ubuntu to install on my laptop with no success. I have tried the booting from a cd a flash drive and wbui. nothing seems to work. I tried both 64bit and 32bit versions all 3 ways. I have even tried fedora 16 with no success. Let me give you a run down of my problem, when booting from the cd i get to the purple flash screen with the keyboard and the other circle thing at the bottom and then a cursor comes up and screen goes black. same thing with fedora. when i did the wbui it would install ok but when i selected ubuntu after restarting the computer it would do the same thing. and just go to black screen and do nothing. I have put ubuntu on my other laptop with no problems what so ever. I have a duel boot with ubuntu and win7 working just fine on that. and im trying to do the same thing with this computer. 
The laptop is a :
Toshiba satellite c675d-s7310 
win7hp x64
4gb ram
AMD e-450apu
Radeon hd6320 

Does anyone have any ideas on whats going on? any help or coments would be greatly appreciated thank you!

---

### Post by heshoots67 on 2012-01-18
Maybe there is a problem in the Laptop you are using.

---

### Post by jbunch on 2012-01-18
well it boots into win7 just fine. not really sure why it would have an issues with booting from a cd, I'm not disagreeing with you it could be the laptops problem but not sure where the problem actually resides.

---

### Post by wildmanne39 on 2012-01-18
Hi, here is a link that should help.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

### Post by jbunch on 2012-01-18
> **wildmanne39 said:**
> Hi, here is a link that should help.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

[SIZE=2]enabling nomodeset[/SIZE] it the kernel options got me past the splash screen but while it was loading the screen cut off again. but this time i could actually hear the little tune that plays when the desktop is done loading. I don't know enough about kernel options to know what else i may need or not need to enable. I really hope that the next version of ubuntu will have support for newer hardware though.

---

### Post by wildmanne39 on 2012-01-18
Hi, did you try all the options in that link one at a time? there are several there and one of them usually works.
Thanks

---

### Post by collisionystm on 2012-01-18
when you boot with nomodeset

can you switch to tty1

CTRL + ALT + F1

---

### Post by Xgen on 2012-01-19
Have you tried with Oneiric Ocelot? If you're trying to install ubuntu previous to Oneiric with an ATI/AMD - specs below - and it fails, then you're in my group. Same symptoms...login sound, blank screen, occasional 'too many connections' error. Can bring up a tty prompt, but no GUI. Also works in Recovery Mode. Haven't found a practical solution yet - it's just a challenge rather than a necessity, as Oneiric and Precise install just fine (and LinuxMint too). But Maverick is (was) my favorite. And yes, all ubuntu versions boot just fine on a previous desktop with an NVidia card.

---

### Post by davethewave83 on 2012-01-19
might be a problem with the Xorg configuration, and because I'm less experienced than a lot of people, what I'd do is install it via Wubi, then boot into the Wubi installation, back the wubi installed files (the ones that boot) up to an external source, boot into a live CD, manually copy the files to the / root drive, not forgetting to chown -R user:user /home 

and that'd likely solve it for me. 

it's a bit of a hassle I guess ;) 

maybe you could improvise and just copy the xorg files over from the working Wubi install into the non-working regular install.

---

### Post by jbunch on 2012-01-20
I was unable to get any of the kernel options to work for me however I was successful installing. 10.4 this morning...everything seems to be working except the wireless and perhaps some display drivers witch I'm sure I can find those once I hook it it up to a hard wired internet connection.  Thanks for all the help guys much appreciated

---

### Post by wildmanne39 on 2012-01-20
Hi, I am glad you got 10.04 installed, after you get a wired connection I can probably help you get the wireless working, just start another thread about wireless and post a link to it here.
Thanks

---

### Post by steentjie on 2012-01-20
I just had the exact same problem on my laptop install. Installing from the live cd worked after setting nomodeset. However on boot after install I once again had a blank screen.

I finally fixed the problem by running nomodeset in place of  quick splash in the edit menu of the grub loader.
I then pressed F10 to boot
Then Ctrl Alt F1 to open a cmd prompt
I then installed gdm in place of lightdm as I had suspicions it may be the cause.

sudo apt-get gdm

#installing this forces you to select gdm or lightdm.

I then updated my graphics card drivers via the command prompt following this guide:
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html)

On reboot it worked.


Im new to Linux and have only been at it for about a week. In that time I have installed Ubuntu 11.10 on 2 x Desktops and 1 x laptop.  Also Ubuntu server on a home based web server.


This problem of blank screens and install problems has happened on all but one of the installs. Where it has been down to lightdm hanging on start up or graphics card driver issue


Regardless of this, I am loving my Ubuntu experience so far and cant believe that I have waited this long to switch.

---

### Post by collisionystm on 2012-01-20
> **steentjie said:**
> I just had the exact same problem on my laptop install. Installing from the live cd worked after setting nomodeset. However on boot after install I once again had a blank screen.

I finally fixed the problem by running nomodeset in place of  quick splash in the edit menu of the grub loader.
I then pressed F10 to boot
Then Ctrl Alt F1 to open a cmd prompt
I then installed gdm in place of lightdm as I had suspicions it may be the cause.

sudo apt-get gdm

#installing this forces you to select gdm or lightdm.

I then updated my graphics card drivers via the command prompt following this guide:
[http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html](http://mygeekopinions.blogspot.com/2011/06/how-to-install-atiamd-catalyst-linux.html)

On reboot it worked.


Im new to Linux and have only been at it for about a week. In that time I have installed Ubuntu 11.10 on 2 x Desktops and 1 x laptop.  Also Ubuntu server on a home based web server.


This problem of blank screens and install problems has happened on all but one of the installs. Where it has been down to lightdm hanging on start up or graphics card driver issue


Regardless of this, I am loving my Ubuntu experience so far and cant believe that I have waited this long to switch.


I can assure you it is not lightdm causing the problem. The issue is with Xorg. You will find that even a gdm distro such as fedora will cause you the same issue.

The best way to handle a blank screen Install with an ATI Card is:

Boot live CD with nomodeset

switch to TTY1 or 2 with CTRL + ALT + F1 ( F2, F3...etc.)

remove the xorg driver

sudo apt-get remove xserver-xorg-video-radeon

sudo lightdm restart

install Ubuntu.

Repeat process. (minus live-cd )

Once in, open terminal

sudo apt-get install fglrx-updates


Install Compiz config settings manager

Open and Select OpenGL
Disable sync to vblank and set texture filter to fast

Open catalyst control center and enable 'Tear Free'

Reboot.

You will be running just peachy. **It is very important to perform the compiz step when finished.**

---

### Post by jbunch on 2012-01-21
> **wildmanne39 said:**
> Hi, I am glad you got 10.04 installed, after you get a wired connection I can probably help you get the wireless working, just start another thread about wireless and post a link to it here.
Thanks
[http://ubuntuforums.org/showthread.php?p=11628257#post11628257](http://ubuntuforums.org/showthread.php?p=11628257#post11628257) 
Thanks!

---

