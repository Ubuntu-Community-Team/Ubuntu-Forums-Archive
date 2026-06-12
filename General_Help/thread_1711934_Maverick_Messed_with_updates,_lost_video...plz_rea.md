---
title: "Maverick: Messed with updates, lost video...plz read"
date: 2011-03-22
forum: General Help
---

### Post by xtremezj on 2011-03-22
I was following the link below on my Acer trying to get my FN brightness adjust keys to actually work, instead of just showing the dialog. 

[http://ubuntuforums.org/showthread.php?t=1636959](http://ubuntuforums.org/showthread.php?t=1636959)

After following the steps and restarting, i can hear ubuntu start and the login screen appear, but i cannot see anything. Brightness keys do not work.

So i hold my left shift to get the boot menu. Neither the primary boot or it's recovery method work (Kernel 2.6.35-28-generic).

However if i choose 2.6.35-27-generic it boots right up like nothing is wrong. So how do i get my primary kernel working right again?

Thanks

---

### Post by xtremezj on 2011-03-22
Bump

I tried to undo the steps (except for running the update manager, no idea how to undo that) and still no dice.

---

### Post by xtremezj on 2011-03-22
Seriously nobody? I have been searching all day

---

### Post by xtremezj on 2011-03-24
and bump again

---

### Post by Krytarik on 2011-03-24
Although I have no experience at all with brightness control or such, the issue seems more related to the running video driver, since you can boot fine with the previous kernel.

What video card/chip do you have?
What driver are you running?
How did you install those?

---

### Post by xtremezj on 2011-03-25
I'm running a Radeon, but it is the same drivers it has been since i installed Maverick the week it came out. I have not updated them, changed them, etc.

The only difference i can find is the kernel, so something happened with the update.

---

### Post by Krytarik on 2011-03-25
Then you are running the default open source driver, not the proprietary one offered by "Additional Drivers"?

Again, what video card/chip do you have!?
You may post the output of
```
lspci |grep VGA
```

---

### Post by xtremezj on 2011-03-26
My mistake, it's the other laptop with the ATI card. This one:

Intel GMA 4500M

printout of lspci:

Blk0psACER:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
04:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
Blk0psACER:~$


I ran today's updates, still no change on the primary kernel. Still having to boot to the second one.

---

### Post by xtremezj on 2011-03-26
one more observation, when it boots with no video on the newest kernel, i have to hold down the power button till it shuts off. RIGHT before the power cuts off in that very last moment, the screen lights up and i can see the "shut down, restart, hibernate" dialog. It's on just long enough for me to know what it is, then it's off.

So odd. I have tried playing with the grub config file to no avail.

---

### Post by Krytarik on 2011-03-26
Try upgrading the video driver through Xorg-Edgers' PPA, it offers more recent drivers than the offical repos:
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade
```If that doesn't help either, you may just stick with old kernel, at least until the next kernel upgrade. That's exactly the reason why one should always retain the previous working kernel.

---

### Post by xtremezj on 2011-03-26
No change.

Can i delete the newest kernel from the grub list, so i can stop hitting the shift key to get my computer up? Also, when the new kernel comes out what if the error persists?

---

### Post by Krytarik on 2011-03-26
> **xtremezj said:**
> 
Can i delete the newest kernel from the grub list, so i can stop hitting the shift key to get my computer up?
I wouldn't remove the current kernel packages, otherwise you would keep getting notified about available updates. Simply change the default boot option:
[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)
> **xtremezj said:**
> 
Also, when the new kernel comes out what if the error persists?
We will see that then.

---

### Post by xtremezj on 2011-03-27
I'll check that out. Thanks a lot, if a future kernel update does not fix it I will bump this thread up.

---

### Post by xtremezj on 2011-03-27
What i didnt notice was that updating the drivers fixed the brightness control, it now works.

So i have a broken kernel, but the original goal was attained lol

---

### Post by Krytarik on 2011-03-27
> **xtremezj said:**
> What i didnt notice was that updating the drivers fixed the brightness control, it now works.

Ah, great then! Then we wait for the next kernel, and see if the main issue re-occurs.

---

