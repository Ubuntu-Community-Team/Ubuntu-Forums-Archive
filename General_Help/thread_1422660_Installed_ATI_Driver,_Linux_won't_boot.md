---
title: "Installed ATI Driver, Linux won't boot"
date: 2010-03-05
forum: General Help
---

### Post by P2000camaro on 2010-03-05
I just installed Ubuntu again after about a year of not using it. Afterward I installed the restricted ATI driver (I have an ATI Mobility card.. I think it's the 3460). Now after GRUB I just get a black screen. I just booted from the CD, but I cannot figure out how to uninstall the driver from here as it's not actually booted to my desktop, just the LIVE CD. Is there any way to get back into Linux without fully reinstalling?

---

### Post by patchwork on 2010-03-05
If you go back to boot off of your hard drive, you should be able to drop to tty1 console when the screen turns black by hitting CTRL+ALT+F1.  Login, and type 

```
lsmod
```

Expect to see your driver listed in the output ( I think ATI uses fglrx or something similar ).  If the module is not loaded, but is installed, try

```
 sudo modprobe fglrx 
```

You also want to make sure your xorg.conf [if your system uses it] has the proper driver listed in the device section.


PS.  you can chroot from the CD, but there should be no need to do that unless you REALLY need to go through this in a GUI

---

### Post by coffeecat on 2010-03-05
Don't re-install just yet.

Are you using Karmic? If, so and you simply delete/rename xorg.conf, the system will automatically use the open source radeon driver. Which may be better.

See if you can identify your graphics card precisely and then search the forums. You might find that the proprietary fglrx driver is bad news with your particular card. In which case deleting xorg.conf is the simplest way of getting into your desktop with the open source driver so that you can uninstall the fglrx driver from the GUI. You can delete xorg.conf either from the live CD, or by booting into recovery mode and doing it from the console.

The possibly good news: on my laptop with the ATI Radeon HD 4200 graphics, the fglrx driver was a complete and unmitigated disaster in Karmic, so I used the delete xorg,conf trick to get the radeon driver back. Which was OK, but no 3D.

But in Lucid alpha, I get compiz (rotating cube, transparency, wobbly windows, the lot) out of the box with the default open source driver.

---

### Post by P2000camaro on 2010-03-05
Thanks a lot guys! I was able to revert back to the original driver and get to my desktop :) Thanks again!

---

### Post by TimK01 on 2010-03-12
I have a similar problem, I installed a Radeon HD5670 Graphics card. initialy the system came up in low graphics mode, I ran the hardware driver tool and it sugested installing fglrx which I did.

Now I boot and get either a black screen with a black and white ubuntu logo and the system freezes  or verticle bars

How do i get rid of the fglrx driver?

---

### Post by howlingmadhowie on 2010-03-12
boot into rescue mode and enter the following:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.oldversion
<your password>

```
and then 
```

sudo init 6

```

the computer will restart and the graphical system will use the default driver rather than fglrx.

---

### Post by TimK01 on 2010-03-12
Thanks howie

---

### Post by coffeecat on 2010-03-12
> **TimK01 said:**
> I have found the X11 directory but cant access it even with sudo, what am i missing?

Did you boot into recovery mode? Were you in a text-only console? If so, you don't need the sudo because in recovery mode you get root powers without a password - so take care!

Boot into recovery mode - that is usually the second choice in the grub menu. After a few seconds of scrolling text you get a simple menu choice. Choose "text console without networking". It might be "root console..." or similar - I'm going from memory here - and you will be presented with a simple # prompt. Then:

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.oldversion
```That will rename the xorg.conf file to make it unavailable to the xserver. Remember that Linux is case-sensitive - you have both capital and lower-case X's in that line. Now you have to reboot, which is simple:

```
reboot
```

---

### Post by TRAFFICBLOWS on 2010-03-26
WOW you guys saved my *** from reinstalling Linux Mint a 3rd time from this issue... thought it was my USB flash drive that was dying!  Thanks!!!!

So this obviously looks to me like there is a major incompatibility between ATI driver and Ubuntu.  Should a bug be reported somewhere?

---

### Post by coffeecat on 2010-03-27
> **TRAFFICBLOWS said:**
> So this obviously looks to me like there is a major incompatibility between ATI driver and Ubuntu.  Should a bug be reported somewhere?

It's more specific than that. The open source 'ati' driver is just fine - except no compositing/3d with some cards. It's the proprietary 'fglrx' driver that is the problem - but again only with **some** cards, and the problem is between the fglrx driver and the xserver, not Ubuntu itself. If you look around the forum, you'll see some people are using the fglrx driver OK. If you want to see whether a bug report has been filed for your card, have a look here:

[https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/)

By the way, when you get to use Ubuntu Lucid or the version of Mint that will be based on Lucid (or at least the version of xserver that will be used in Lucid) you may find the open source ati driver adequate for your needs and you may not need the proprietary driver. I'm posting from Lucid on a laptop with the Radeon HD4200 graphics and the ati driver and I'm getting compiz special effects quite nicely. Ymmv, depending on your graphics card.

---

### Post by hawkiye on 2011-12-06
> **patchwork said:**
> If you go back to boot off of your hard drive, you should be able to drop to tty1 console when the screen turns black by hitting CTRL+ALT+F1.  Login, and type 

```
lsmod
```Expect to see your driver listed in the output ( I think ATI uses fglrx or something similar ).  If the module is not loaded, but is installed, try

```
 sudo modprobe fglrx 
```You also want to make sure your xorg.conf [if your system uses it] has the proper driver listed in the device section.


PS.  you can chroot from the CD, but there should be no need to do that unless you REALLY need to go through this in a GUI

 I am a little lost here I need to revert back to the open aATI drivers and I can't boot. So if I get to the console is this all I need to type in to get rid of the proprietary drivers? Or is thee another step?

---

### Post by Mark Phelps on 2011-12-07
> **hawkiye said:**
> I am a little lost here I need to revert back to the open aATI drivers and I can't boot. So if I get to the console is this all I need to type in to get rid of the proprietary drivers? Or is thee another step?

You really shouldn't hijack someone else's old thread; instead, you should start your own.

Removing the fglrx drivers and replacing them with the open source Radeon drivers is covered below:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

