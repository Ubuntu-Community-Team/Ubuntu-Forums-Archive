---
title: "Ubuntu 12.04 freezes"
date: 2012-07-17
forum: General Help
---

### Post by leopoldbirkholm on 2012-07-17
Hello,

**My rig**
Acer eMachines E443 with AMD DualCore E300, AMD Radeon HD 6310 GPU, 4 GB RAM DDR3 laptop
**My problem**
I have tried Linux Mint 13 Maya and Linux Ubuntu 12.04 Precise Pangolin with the same issue. After log in the system freezes. Sometime after a minute, sometimes when I got the update manager running. I have read through this thread from [Linux Mint forum](http://forum.linuxmint.com/viewtopic.php?f=90&t=103054&start=280) and [Ask Ubuntu topic "What should I do when Ubuntu freezes?"](http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717).

I have tried all steps in the thread from Mint and the guide from Ask Ubuntu. Power-cycling, the REISUB, CTRL+ALT+Del. All steps. But the only thing left is yank the power cord or press down the power button to force it to shut down. After the power-cycle and reboot, same issue.

I have removed all USB-things like memory stick, modem for mobile broadband and fan (I have it on a cooling pad).

What more can I do? I don't want to go back to Windows. :confused:

---

### Post by kmsalex on 2012-07-17
can you get a stable desktop long enough to install drives?
You'd have to manage to get the "additional Drives" program open.

---

### Post by d4m1r on 2012-07-17
Try logging in with Unity 2D instead or install Gnome via command line and see if that freezes it?

---

### Post by techvish81 on 2012-07-17
do you have chrome/ chromium installed. ?

---

### Post by Ashtonford on 2012-07-18
> **leopoldbirkholm said:**
> Hello,

**My rig**
Acer eMachines E443 with AMD DualCore E300, AMD Radeon HD 6310 GPU, 4 GB RAM DDR3 laptop
**My problem**
I have tried Linux Mint 13 Maya and Linux Ubuntu 12.04 Precise Pangolin with the same issue. After log in the system freezes. Sometime after a minute, sometimes when I got the update manager running. I have read through this thread from [Linux Mint forum](http://forum.linuxmint.com/viewtopic.php?f=90&t=103054&start=280) and [Ask Ubuntu topic "What should I do when Ubuntu freezes?"](http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717).

I have tried all steps in the thread from Mint and the guide from Ask Ubuntu. Power-cycling, the REISUB, CTRL+ALT+Del. All steps. But the only thing left is yank the power cord or press down the power button to force it to shut down. After the power-cycle and reboot, same issue.

I have removed all USB-things like memory stick, modem for mobile broadband and fan (I have it on a cooling pad).

What more can I do? I don't want to go back to Windows. :confused:



I had the same prob just use mint 12 instead of 13 and use cinnimin it works fine with it.  Ubuntu 12.04 and mint 13 both need time to get more stable, updates etc.

---

### Post by leopoldbirkholm on 2012-07-18
> **kmsalex said:**
> can you get a stable desktop long enough to install drives?
You'd have to manage to get the "additional Drives" program open.

No. Just log on and trying to locate the update manager via Dash and freeze.

EDIT: Got so far to get the device manager up to install the proparity AMD drivers but middle of download the system froze.

---

### Post by leopoldbirkholm on 2012-07-18
> **techvish81 said:**
> do you have chrome/ chromium installed. ?

No, I have not yet got that far.

---

### Post by leopoldbirkholm on 2012-07-18
Now the system freeze at the log on screen. This is not looking good.

---

### Post by leopoldbirkholm on 2012-07-18
> **Ashtonford said:**
> I had the same prob just use mint 12 instead of 13 and use cinnimin it works fine with it.  Ubuntu 12.04 and mint 13 both need time to get more stable, updates etc.

Thank you. I have downloaded and installed Linux Mint 12 Lisa X86. It works better now but still it freeze. I got so far I updated the system via the Terminal. But at something called "mrege" or similar, the system froze and I was force to restart it. Then the mouse stop working and some of the graphic also.

---

### Post by leopoldbirkholm on 2012-07-18
So far, this is what made it work for me.

Download and burned out the Linux Mint 12 Lisa X86 no codec version for fit on a CD-R. I then connected my laptop to the network via Ethernet.

In with the disc and run the live environmental. Open the Terminal. Run this code:
```
sudo apt-get update
```

After Mint have updated itself, run the installation. When the installation is complete, click onto "Continue test". Open up the Terminal again.
```
sudo apt-get update
sudo apt-get upgrade
gnome-session-quit --power-off

```
Hit enter to power off. When prompt, remove the disc and hit enter again.

Boot up again and run the update via Terminal again. It works right now with Mint.

---

### Post by leopoldbirkholm on 2012-07-19
Hm. I thinking I am funding the root of the problem. I have a 3G mobile broadband and the USB-modem seem to cause problem. Hello Google, do you have any answers for me?

---

### Post by kmsalex on 2012-07-23
> **leopoldbirkholm said:**
> Hm. I thinking I am funding the root of the problem. I have a 3G mobile broadband and the USB-modem seem to cause problem. Hello Google, do you have any answers for me?

I kind of assumed you did the first step of trouble shooting of un-pluging all un-nesacery devices...

---

### Post by leopoldbirkholm on 2012-07-25
> **kmsalex said:**
> I kind of assumed you did the first step of trouble shooting of un-pluging all un-nesacery devices...

I did that on my second try. First I installed Ubuntu with my mobile broadband in order to download updats, codes and whatnot. But freezing came and so I stop using my mobile broadband. Then it worked a little better but still it froze from time to time. So I unplugged and did a clean install of Linux Mint 12 as suggested. Everything was humming so I tried again to use my mobile broadband. And then the system break down. It start freezing with or without the mobile broadband.

So right now I am trying Fedora 17 LXDE and that is humming nicely. It's not Debian-based so it is a lot to learn.

Sadly, it seems I can't use my mobile broadband on Linux. The hardware seems to cause meltdown in the system.

**[SIZE="2"]I am sorry if I was unclear on the USB things attached. My only excuse is English is my second language.[/SIZE]**:oops:

---

### Post by leopoldbirkholm on 2012-07-25
The cause of meltdown for my Ubuntu and Mint installation on a Acer eMachine E443 is an Huawei E1820 mobile broadband USB modem. Using the same modem on a Fedora installation does not cause the same meltdown. So, my solution for now is to switch to Fedora on the Acer.

---

