---
title: "Can't hear sound on Ubuntu through my speakers"
date: 2009-12-27
forum: General Help
---

### Post by NeverMind785 on 2009-12-27
I just downloaded Ubuntu 9.10 and when my headphones are in I can hear everything fine. When I have my headphones out, I hear nothing at all. What's going on? :confused:

I have a Toshiba NB205-N325BL with 1gb of ram and about 100gb of memory left on my harddisk. (If that helps any)

---

### Post by NeverMind785 on 2009-12-27
bump. help. :(

---

### Post by Vaphell on 2009-12-27
run lspci in terminal
look for 'audio device' part - this is an essential piece of information. Code of the chipset will help to narrow it down

---

### Post by drdanielfc on 2009-12-27
I would say this is more likely hardware than software - you may have bent the headphone jack pin so it always thinks that your headphones are plugged in (I did this once).

Assuming it is a software error, if you right click on the sound icon>Sound Preferenced>Output, what do you see? Also please post the settings located in your hardware tab 

~Dan

---

### Post by NeverMind785 on 2009-12-27
I get this

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by NeverMind785 on 2009-12-27
It says Internal Audio Analog Stereo in sound preferences

---

### Post by drdanielfc on 2009-12-27
Mind posting a screenshot of the hardware tab?

---

### Post by NeverMind785 on 2009-12-27
sorry, im a noob.

How?

---

### Post by drdanielfc on 2009-12-27
Go back into the sound preference, click the hardware tab, and hit "prt scn" on your keyboard (if your using a laptop you my have to hold the "fn" key. It will prompt you to save a file. Save it to your desktop and attach the file to this thread.

---

### Post by NeverMind785 on 2009-12-27
heres the screenshot

---

### Post by Vaphell on 2009-12-27
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318)

it appears that the problem is known and worked on

---

### Post by drdanielfc on 2009-12-27
I'm off to bed now but try checking your headphone jack to see if its bent. If not, I'll see if I can help you tommorrow. Good luck!

---

### Post by NeverMind785 on 2009-12-27
Well what exactly do I do to fix it?

---

### Post by Chris Edgell on 2009-12-27
I sincerely recommend that you go to this site:

[http://ubuntuforums.org/showthread.php?p=8568763#post8568763](http://ubuntuforums.org/showthread.php?p=8568763#post8568763)

Take a look, take a quick scan right now before you  try fixing something more serious,  I'm thinking something may just be muted and I have outlined in very simple language how to check.  I'm hoping it's not too different from mine, Jaunty 9.04

---

### Post by NeverMind785 on 2009-12-27
It's not the same as 9.10. It confuses me.

---

### Post by Chris Edgell on 2009-12-27
Well, I'll keep track of your thread and see if you solve it.  I sure hope you do, but if you don't I'll try to get somebody to walk you through the steps to check these 2 or 3 places to make sure external speaker, or amp or ext. is not muted or not activated as there has been a lot of that lately.

Again good luck!

---

### Post by NeverMind785 on 2009-12-28
> **Vaphell said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/438318)

it appears that the problem is known and worked on

How do I patch Ubuntu? :shock:

---

### Post by drdanielfc on 2009-12-28
> **Chris Edgell said:**
> Well, I'll keep track of your thread and see if you solve it.  I sure hope you do, but if you don't I'll try to get somebody to walk you through the steps to check these 2 or 3 places to make sure external speaker, or amp or ext. is not muted or not activated as there has been a lot of that lately.

Again good luck!

The fact that he can hear it with the headphones plugged in causes me to overrule that possibility, unless there is a second setting that may have been messed up?

---

### Post by NeverMind785 on 2009-12-28
> **drdanielfc said:**
> The fact that he can hear it with the headphones plugged in causes me to overrule that possibility, unless there is a second setting that may have been messed up?

If so, where could I find the setting? I've already checked the terminal, 2 alsa mixer programs, and my sound preferences.

---

### Post by drdanielfc on 2009-12-28
I'm not sure - perhaps something went wrong in the install. Can you get sound via a live cd?

---

### Post by NeverMind785 on 2009-12-28
> **drdanielfc said:**
> Can you get sound via a live cd?

Sadly, I have a netbook.

I have also reinstalled already and that didn't work. The sound works fine on Windows 7 but not on ubuntu. So it isn't a hardware problem. We can rule that out.

Apparently this is a frequent problem because a Canonical worker made a patch for it. I have the patch file but I don't actually know how to use the file. If I figure that out, it should be fixed.

---

### Post by drdanielfc on 2009-12-28
> **NeverMind785 said:**
> Sadly, I have a netbook.

I have also reinstalled already and that didn't work. The sound works fine on Windows 7 but not on ubuntu. So it isn't a hardware problem. We can rule that out.

Apparently this is a frequent problem because a Canonical worker made a patch for it. I have the patch file but I don't actually know how to use the file. If I figure that out, it should be fixed.

Lets see the file perhaps I can help

---

### Post by NeverMind785 on 2009-12-28
[http://patchwork.kernel.org/patch/49477/](http://patchwork.kernel.org/patch/49477/)

at this link

---

### Post by NeverMind785 on 2009-12-28
bump

---

