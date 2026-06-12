---
title: "Ubuuntu 10.04 hangup"
date: 2011-06-29
forum: General Help
---

### Post by monikapatira@gmail.com on 2011-06-29
Please help me to resolve th problem stated underneath:
My computer(P4, 512MB RAM) running Ubuntu 10.04 hangs unexpectedly after  certain period of inactivity (4-5 minutes maybe). I checked power  management settings and all power saving options are set to off.

The  screen says Checking battery state comes for  a while... and then black  screen with stripes comes. Monitor also goes  off for say a sec or  two.Then monitor goes 'on'  on its own .

 This process of Black screen with stripes, monitor off and on goes on until I "Reboot"

Please help me.

---

### Post by jerrrys on 2011-06-29
will it do the same with your laptop plugged in to power supply?

---

### Post by amjjawad on 2011-06-29
> **monikapatira@gmail.com said:**
> Please help me to resolve th problem stated underneath:
My computer(P4, 512MB RAM) running Ubuntu 10.04 hangs unexpectedly after  certain period of inactivity (4-5 minutes maybe). I checked power  management settings and all power saving options are set to off.

The  screen says Checking battery state comes for  a while... and then black  screen with stripes comes. Monitor also goes  off for say a sec or  two.Then monitor goes 'on'  on its own .

 This process of Black screen with stripes, monitor off and on goes on until I "Reboot"

Please help me.

Hello and Welcome :)

Is this a new fresh installation?
What kind of Graphics Card do you have?
Does reboot fix the issue?
Did you try to disable Screen Saver?

And don't forget to answer the first Q on the previous post :)

---

### Post by monikapatira@gmail.com on 2011-06-30
> **jerrrys said:**
> will it do the same with your laptop plugged in to power supply?

I am using desktop and not laptop

---

### Post by monikapatira@gmail.com on 2011-06-30
> **amjjawad said:**
> Hello and Welcome :)

Is this a new fresh installation?
What kind of Graphics Card do you have?
Does reboot fix the issue?
Did you try to disable Screen Saver?

And don't forget to answer the first Q on the previous post :)

**1.Yes ubuntu 10.04 is my fresh installation desktop**
2.**regarding graphics card: Please see beneath**
monika@monika:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10[B])

3. Yes Reboot solves the problem temporarily. Again inactivity for few minutes makes the problem repeat.[/B]

**4.It occurs before the screensaver gets activated. Duration of screen saver is 1 minute.**

---

### Post by amjjawad on 2011-06-30
> **monikapatira@gmail.com said:**
> **1.Yes ubuntu 10.04 is my fresh installation desktop**
2.**regarding graphics card: Please see beneath**
monika@monika:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10[B])

3. Yes Reboot solves the problem temporarily. Again inactivity for few minutes makes the problem repeat.[/B]

**4.It occurs before the screensaver gets activated. Duration of screen saver is 1 minute.**

So you have set your screen saver to start after 1 min of inactivity?

What's the screen saver you have chosen? I have something similar to your case when I choose something else rather than "Blank or Black Screen".

Perhaps I'm wrong but let's try that.

If that's not the case, it might be something wrong with the driver for your Graphics Card.

---

### Post by monikapatira@gmail.com on 2011-07-07
> **amjjawad said:**
> So you have set your screen saver to start after 1 min of inactivity?

What's the screen saver you have chosen? I have something similar to your case when I choose something else rather than "Blank or Black Screen".

Perhaps I'm wrong but let's try that.

If that's not the case, it might be something wrong with the driver for your Graphics Card.
**This hang up has no relation with screen saver as I feel . It happens  before screen saver a(flaoting feet - 1 minute) actually gets  activated.**
 
 **My system was not starting in linux( I have dual boot - Linux and  windows) at all before 3-4 days , Windows was running absolutely fine. I  then formatted ubuntu10.04 and reinstalled it. But the problem is still  there. Now Screen saver is black screen and is after 5 minutes.**
 
 [B]
I feel Graphics card is fine as windows has got no problem[/B]

---

### Post by amjjawad on 2011-07-08
> **monikapatira@gmail.com said:**
> **This hang up has no relation with screen saver as I feel . It happens  before screen saver a(flaoting feet - 1 minute) actually gets  activated.**
 
 **My system was not starting in linux( I have dual boot - Linux and  windows) at all before 3-4 days , Windows was running absolutely fine. I  then formatted ubuntu10.04 and reinstalled it. But the problem is still  there. Now Screen saver is black screen and is after 5 minutes.**
 

Disable the Screen Saver and check. If the problem will occur again, then maybe the driver of your Graphics Card is not installed probably.


 [B]> 
I feel Graphics card is fine as windows has got no problem[/B]

[Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm") :)

Have you tried to Run Ubuntu from the LiveCD?
will the same happen if you run Ubuntu from the LiveCD?

---

### Post by monikapatira@gmail.com on 2011-07-14
> **amjjawad said:**
> Disable the Screen Saver and check. If the problem will occur again, then maybe the driver of your Graphics Card is not installed probably.


 [B]

[Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm") :)

Have you tried to Run Ubuntu from the LiveCD?
will the same happen if you run Ubuntu from the LiveCD?

I have not tried running ubuntu from LIVE CD. 
I feel the problem is when the mouse is inactive for few minutes/ seconds. If I keep mouse active the problem does not activate. 
After problem starts I get, 
PULSE AUDIO CONFIGURED FOR PER USER SESSION . ENABLING ADDITIONAL EECUTABLE BINARY FORMAT. BINFMT SUPPORTED [OK]
CHECKING BATTERY STATE [OK]. 
 Then the black screen cones with stripes...
I have to finally restart.

---

### Post by cccc on 2011-07-18
1.) create /etc/X11/xorg.conf```

# Xorg -configure
# cp /root/xorg.conf.new /etc/X11/xorg.conf
``` 

2.) put the following in /etc/X11/xorg.conf in Section "Device":```

Section "Device"
Identifier "Card0"
Driver "intel"
**Option "Shadow" "true"**
**Option "DRI" "false"**
**BoardName "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)"**
BusID "PCI:0:2:0"
EndSection
```

Run "lspci | grep VGA" to find out the "BusID" and the "BoardName", for example:```

# lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

---

