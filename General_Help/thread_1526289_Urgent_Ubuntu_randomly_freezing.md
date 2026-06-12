---
title: "Urgent: Ubuntu randomly freezing"
date: 2010-07-07
forum: General Help
---

### Post by Tandyman100 on 2010-07-07
I just installed Ubuntu 9.04 from a CD I got from Canonical some time ago, immediately upgrading the fresh install from 9.04 to 9.10, and then to 10.04. However, the disk I have is x86, and the CPU is a brand-new Phenom X2 box (so AMD64). Now, I've been installing WINE, VirtualBox, Docky, and OpenArena, and that's it. I've also been trying to re-map the individual /home directories to the /my documents directories on my Windows HDD, but that's another story. Now, the computer will randomly lock up, not responding to any key combinations or mouse moves/clicks. This usually happens when it turns off the monitor after being left for a while, but has just started (keep in mind this installation has only existed for a day and a half) locking up whilst browsing files and doing other general work on the PC.

Any ideas on what could be causing this and what I can do to remedy it?

---

### Post by mörgæs on 2010-07-08
You are asking a lot of questions. Let's take it in small bites. 

Since the computer is newly installed I guess that you don't have anything of value on it. How does it behave if you wipe the whole system and install a fresh 10.04 (not upgrading)? 

[http://www.releases.ubuntu.com/lucid/](http://www.releases.ubuntu.com/lucid/)

When this has been stable for a while it is time to install Wine and the other packages.

---

### Post by Tandyman100 on 2010-07-08
Well, I have done a LOT of configging and installing programs... is there a way to back up just what I have changed in the OS since I installed it, and then restore from that when I fresh install?

---

### Post by mörgæs on 2010-07-09
I don't know of such option, and I don't think that it would help you getting a stable system.

Again, I would recommend beginning with a plain vanilla setup and then modify in small steps, testing each step thoroughly before proceeding. 

Also, it is easier for people in the forum to give advice, if your system has not been customised to much.

---

### Post by Tandyman100 on 2010-07-14
Sorry for the delay. I downloaded Ubuntu 10.04 AMD64 and installed it side-by-side with my 'old' installation, got updates, and installed the proprietary video drivers, and left the PC for the evening. When I got back a few hours later, the computer was completely frozen.

This is literally brand-new hardware, and I never had even an inkling of a problem with Windows, tho I did have a problem with SUSE.

---

### Post by mörgæs on 2010-07-14
Which screen card do you have? Please post the output of 

```
hwinfo --gfx
```

---

### Post by Tandyman100 on 2010-07-15
```
31: PCI 100.0: 0300 VGA compatible controller (VGA)             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_9498
  Unique ID: VCu0.sONTTjvJNxF
  Parent ID: _Znp.NfWwNi5KJ96
  SysFS ID: /devices/pci0000:00/0000:00:02.0/0000:01:00.0
  SysFS BusID: 0000:01:00.0
  Hardware Class: graphics card
  Model: "ATI RV730 PRO [Radeon HD 4650]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x9498 "RV730 PRO [Radeon HD 4650]"
  SubVendor: pci 0x1787 "Hightech Information System Ltd."
  SubDevice: pci 0x2269 
  Driver: "fglrx_pci"
  Driver Modules: "fglrx"
  Memory Range: 0xd0000000-0xdfffffff (rw,prefetchable)
  Memory Range: 0xfdee0000-0xfdeeffff (rw,non-prefetchable)
  I/O Ports: 0xee00-0xeeff (rw)
  Memory Range: 0xfde00000-0xfde1ffff (ro,prefetchable,disabled)
  IRQ: 29 (921518 events)
  I/O Ports: 0x3c0-0x3df (rw)
  Module Alias: "pci:v00001002d00009498sv00001787sd00002269bc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is not active
    Driver Activation Cmd: "modprobe radeon"
  Driver Info #1:
    Driver Status: fglrx is active
    Driver Activation Cmd: "modprobe fglrx"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #10 (PCI bridge)

```


Thanks for your help!

---

### Post by alphacrucis2 on 2010-07-15
> **Tandyman100 said:**
> 


Thanks for your help!

It might be worth trying a later fglrx release rather than the one in the Ubuntu repos. The latest Catalyst driver for Linux 64 can be downloaded from AMD's website. To install it, take a look at this howto:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by mörgæs on 2010-07-15
This is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565790](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/565790)
There are some good links in the bug report. It seems like adding boot parameters can do the trick.

You could also install 9.10 and see how he behaves.


By the way, would be good if you added something like "ATI Radeon HD 4650 fglrx" in the thread title. Might help others.

---

### Post by emoguitarist06 on 2010-07-15
> **Tandyman100 said:**
> Sorry for the delay. I downloaded Ubuntu 10.04 AMD64 and installed it side-by-side with my 'old' installation, got updates, and installed the proprietary video drivers, and left the PC for the evening. When I got back a few hours later, the computer was completely frozen.

This is literally brand-new hardware, and I never had even an inkling of a problem with Windows, tho I did have a problem with SUSE.

I definately feel your pain! This is a known issue for hundreds/thousands of users.
See this forum: [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)
No clear answer yet and what's causing the problem

I personally had a fresh install of 10.04 and I finally got fed up and I did a fresh install of 9.10 and I am completely happy.
I'm just going to wait until 10.10

---

### Post by Tandyman100 on 2010-07-16
> **emoguitarist06 said:**
> I definately feel your pain! This is a known issue for hundreds/thousands of users.
See this forum: [http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)
No clear answer yet and what's causing the problem

I personally had a fresh install of 10.04 and I finally got fed up and I did a fresh install of 9.10 and I am completely happy.
I'm just going to wait until 10.10

I installed the AMD drivers, and it still freezes, so it looks like I'll just have to put up with this random freezing until the next release? That's quite inconvienient, but that forum seems to be hitting the nail on the head as to the problem I'm having.

---

### Post by dreamsR4living on 2010-07-16
> Now, the computer will randomly lock up, not responding to any key combinations or mouse moves/clicks.

I have encountered this problem ever since Ubuntu 8.04 ([http://ubuntuforums.org/showthread.php?t=765510](http://ubuntuforums.org/showthread.php?t=765510)) on different sets of new and older hardware, mainly laptops with 8.04, 8.10 and 10.04. Thousands of people have been affected by it and still there is no clear answer where the problem is coming from.

Advice, stay with an older Ubuntu version that works stable on your computer or if you're in for a challenge, install [Debian]("http://www.debian.org"), which is way more stable than Ubuntu and never froze on me, but more difficult to install and configure.

---

### Post by mörgæs on 2010-07-16
I agree with dreamsR4living. Don't assume that new means better. It is a common occurrence that an older version is more stable than the new one. What matters is that the version is supported.

New *could* be better, and if you want to give 10.10 a chance, it is here:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

You know the warnings: This is a release in development, and it changes without warning (and so on and so on).

---

