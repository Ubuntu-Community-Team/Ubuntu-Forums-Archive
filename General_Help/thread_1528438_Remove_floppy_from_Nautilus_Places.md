---
title: "Remove floppy from Nautilus Places?"
date: 2010-07-10
forum: General Help
---

### Post by Superorb on 2010-07-10
Is there a way to get rid of the floppy entry in the Places? This is not the bookmarks area (which is below) so I can't just right-click and remove or remove it from Bookmarks spot. I already tried commenting the floppy in fstab and then removed the entire line to no avail. Floppy drive is disabled in the Bios, I haven't had a floppy drive in 10+ years. Any ideas?

---

### Post by robsoles on 2010-07-11
Thanks to your post I have just discovered that in 10.04 AMD64 I can no longer access floppy disks in my USB floppy disk drive!!!

When I plug it in I can find it in 'Computer' but no other reference to it appears to be made whatsoever. When I unplug it the icon in 'Computer' disappears again for me.

I am going to troubleshoot my apparent problem a little while I also contemplate yours - what I thought I was going to prove (to myself, before posting on your thread here) was that it is likely that a device is registering a floppy disk drive on your system and Nautilus is just showing it to you.


Can you think of any thing(s) you did just before it appeared that may be associated with it appearing?

What is the result of selecting it in the 'places' area? (sort of expecting 'no media'/'no medium' error)

Can you insert media to each of those "Generic Storage Device"s and try selecting FDD in 'places' again each time - what is result?

---

### Post by Superorb on 2010-07-11
> **robsoles said:**
> 
Can you think of any thing(s) you did just before it appeared that may be associated with it appearing?

It has always been there since I installed 10.04, but I haven't had Ubuntu on this PC in years and I don't remember if it was ever there in an earlier version of Ubuntu.
> 
What is the result of selecting it in the 'places' area? (sort of expecting 'no media'/'no medium' error)

Nothing happens. Even when I right click to open in new window nothing happens.
> 
Can you insert media to each of those "Generic Storage Device"s and try selecting FDD in 'places' again each time - what is result?
It's a multi-card reader. I only have a CF card, but when I insert one it changes from Generic Drive to Generic Drive - CF Card. It pops up under the Floppy entry with the eject icon next to it. No change in Floppy though; nothing happens when I click it either.

Something is reporting a floppy drive and I can't figure out what.

---

### Post by robsoles on 2010-07-11
Please post your results for typing 'lsusb' and 'lspci' into terminal

---

### Post by Superorb on 2010-07-11
LSUSB:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a5f:0006 Zebra 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c505 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05e3:0760 Genesys Logic, Inc. USB 2.0 Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


LSPCI

00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
03:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
05:00.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)

---

### Post by Superorb on 2010-07-11
I looked in the BIOS again, and the floppy was mentioned in two places. It was only disabled in one, so I disabled it in the 2nd place and sure enough "floppy" is gone from places.

Thanks for the help guys. I'll start another thread on how to remove all those "generic storage device" since I only use 1 of the 4 shown.

---

### Post by robsoles on 2010-07-11
I have to take off for work in a couple of minutes but I can probably check in from there anyway.

Those didn't reveal a culprit for me, please try

```
sudo lshw
```

into terminal and copy (hopefully) more extensive info from that one to next post.

---

### Post by Superorb on 2010-07-11
> **robsoles said:**
> I have to take off for work in a couple of minutes but I can probably check in from there anyway.

Those didn't reveal a culprit for me, please try

```
sudo lshw
```

into terminal and copy (hopefully) more extensive info from that one to next post.
Please see the post above yours.

---

### Post by robsoles on 2010-07-11
> **Superorb said:**
> Please see the post above yours.


Then perhaps you could use 'thread tools' at top of this page to mark this thread as solved.

---

### Post by Superorb on 2010-07-11
> **robsoles said:**
> Then perhaps you could use 'thread tools' at top of this page to mark this thread as solved.
I hadn't noticed that before, thanks.

---

