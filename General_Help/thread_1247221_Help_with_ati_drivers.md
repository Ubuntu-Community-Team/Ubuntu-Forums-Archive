---
title: "Help with ati drivers"
date: 2009-08-22
forum: General Help
---

### Post by cj1094 on 2009-08-22
Can someone guide me through the process of installing ati drivers on ubuntu 8.04.3 hardy. Because I couldnt seem to get it to work.

---

### Post by Vakman on 2009-08-22
Which drivers are you attempting to install. What card do you have t, if you are unsure post the output of ```
lspci
```
Also follow [this]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method") and it will walk you through the steps. Or use the Jaunty (9.04) tutorial on that same wiki in the link.
Let me know if you need any more help.

---

### Post by cj1094 on 2009-08-22
00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.4 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 5
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIB (ICH10) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442
01:00.1 Audio device: ATI Technologies Inc Unknown device aa30
03:00.0 IDE interface: JMicron Technologies, Inc. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

My card is an ATI Radeon HD4850

---

### Post by Choose on 2009-08-22
Go to System > Administration > Hardware Drivers

after opening > hardware driver's it should automatically search for the driver you want,then just install it and activate the driver,when it's installed it'll probably ask you to do a restart,if everything has gone ok and you've logged back into the desktop go back to > Hardware Drivers and it should say Ati fglrx driver activated,good luck ;)

---

### Post by Vakman on 2009-08-22
> **Choose said:**
> Go to System > Administration > Hardware Drivers

after opening > hardware driver's it should automatically search for the driver you want,then just install it and activate the driver,when it's installed it'll probably ask you to do a restart,if everything has gone ok and you've logged back into the desktop go back to > Hardware Drivers and it should say Ati fglrx driver activated,good luck ;)

I actually have this exact card and these drivers here rarely work out for me, on any machine. I also assume he has tried this. 
To the OP, did you attempt to follow the instructions in the link I sent? [http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Install_Method) is the link in case you missed it in the last post. Though it is worthwhile to try the System > Hardware Drivers method to install them if you haven't already.

---

### Post by cj1094 on 2009-08-22
Ubuntu doesn't recognize my card. Also there is no System > Preferences > Display. When I was using the livecd I could install drivers, but when I restarted they were gone so I decided to eventually install Ubuntu. Also on livecd I could change my dual monitor positions and it also showed that I have 2 monitors and not just one..

Because display does not show up in preferences I now have to use:
```
gnome-display-properties
```
and gets annoying. Just recently gnome-display-properties stop working when I used it with terminal with the error:
```

No protocol specified

(gnome-display-properties:31567): Gtk-WARNING **: cannot open display: :0.0

```

I am going to try the guide [COLOR=Black][Thisislaw]("http://ubuntuforums.org/member.php?u=627441")[/COLOR] mentioned

---

### Post by cj1094 on 2009-08-22
Now everything I try to launch on Ubuntu just crashes looks like I'm going to reinstall again.

I can't close this firefox session or I won't be able to open it again. Looks like it was from one of the commands in the tutorial Thisislaw directed me too.

I really want to get 8.04 to work because I want to use Userful Multiplier.

---

### Post by Vakman on 2009-08-22
> **cj1094 said:**
> Now everything I try to launch on Ubuntu just crashes looks like I'm going to reinstall again.

I can't close this firefox session or I won't be able to open it again. Looks like it was from one of the commands in the tutorial Thisislaw directed me too.
I find this quite unlikely. Let's do this a different way. To start with, boot into recovery mode and drop to shell and run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` while in recovery mode. This will reset the xserver to the default and may fix the command you said you had to run. Then we will go and install the drivers.

---

### Post by cj1094 on 2009-08-22
Ok I am now ready to start with drivers.

---

### Post by Vakman on 2009-08-22
> **cj1094 said:**
> Ok I am now ready to start with drivers.
So you did enter that in recovery mode and it fixed issues?
You could try using EnvyNG to install the drivers. [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)
For Envy. Has a GUI so should be easy. Try it first. But I would follow the original tutorial I sent you, should work great.

---

### Post by cj1094 on 2009-08-22
I found out what made stuff open then suddenly close and it was the following on the tutorial.

```
sudo depmod -a
```

So I logged out and logged in and will try the rest.

---

### Post by cj1094 on 2009-08-22
As of right now this has not worked. I installed the drivers and now I have to run in low graphics mode. Comes up as MESA rendering. My card does show both monitors, but the system shows it as one. So I cannot split them. Still no proprietary drivers. Ubuntu hasn't detected my graphics card either.

Right now I'm installing EnvyNG and will post once I see if it works. I tried the tutorial you sent me, but did not work.

---

### Post by cj1094 on 2009-08-22
THANK YOU ENVYNG WORKED!!!! WOO HOO!!!!

But, I still do have a problem I can't setup my monitors.

---

### Post by jovianchiron on 2009-08-22
so i tried fixing some of my ati drivers so i could get a second monitor to work, and now my first monitor does not work. what can i do to revert to previous settings?

---

### Post by Vakman on 2009-08-23
Glad that EnvyNG worked out for you.
Try following [http://ubuntuforums.org/showthread.php?t=983781&highlight=dual+monitor+howto+ati](http://ubuntuforums.org/showthread.php?t=983781&highlight=dual+monitor+howto+ati) to setup dual monitors.
Also make sure
> **Temüjin said:**
> If you're trying to run a "big desktop" (not cloned), make sure you have the following in your device section:
```
Option      "EnableRandR12" "false"
Option      "DesktopSetup" "horizontal"
```
you have this in your device section of Xorg. Someone said this will fix things possibly along with the HowTo.

---

