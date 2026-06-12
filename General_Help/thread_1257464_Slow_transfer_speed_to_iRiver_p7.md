---
title: "Slow transfer speed to iRiver p7"
date: 2009-09-03
forum: General Help
---

### Post by xenogia on 2009-09-03
Hi guys,

I recently purchased a iRiver P7 which works great under Linux, but the transfer speeds are ridiculously slow.  They sit around at 80k per second to the device.  Is there a reason why this would be going so slow.

I am currently 9.04 64bit on an Asus P5Q motherboard.  I've actually loaded up Win XP VM to see if it would happen under the VM and the transfer speeds are fine under the VM.  Any suggestions?

---

### Post by morningcrafter on 2009-09-14
I wish someone had some response to this...I've been looking into the p7. Aside from the slow transfer speeds, is it largely compatible with 9.04?

---

### Post by xenogia on 2009-09-14
It is largely compatible with 9.04 minus the slow transfer speeds.  Shame no-one replied to my thread.

---

### Post by feedmecmoore on 2009-09-18
I just got one of these and I'm having the same problem.

The file transfer is unusably slow.  While it is going, dmesg outputs the following lines around once per second:
```

[ 8803.738186] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 8803.738198] end_request: I/O error, dev sdc, sector 979048

```Where the sector number is constantly changing. These lines continue after trying to stop a transfer and I can't unmount the device.

Using Ubuntu 9.04 64bit.  When I get a chance, I'll try in 32bit ubuntu and windows.

---

### Post by xenogia on 2009-09-18
> **feedmecmoore said:**
> I just got one of these and I'm having the same problem.

The file transfer is unusably slow.  While it is going, dmesg outputs the following lines around once per second:
```

[ 8803.738186] sd 8:0:0:0: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_RETRY
[ 8803.738198] end_request: I/O error, dev sdc, sector 979048

```Where the sector number is constantly changing. These lines continue after trying to stop a transfer and I can't unmount the device.

Using Ubuntu 9.04 64bit.  When I get a chance, I'll try in 32bit ubuntu and windows.

Yeah I checked yesterday and got a similar message, a bug perhaps :/

---

### Post by feedmecmoore on 2009-09-18
> **feedmecmoore said:**
> 
  When I get a chance, I'll try in 32bit ubuntu and windows.

Windows works, 32bit ubuntu has the same issue.  I've also notice that the first couple dozen Mb zip by, but then it hits a wall.

---

### Post by xenogia on 2009-09-18
> **feedmecmoore said:**
> Windows works, 32bit ubuntu has the same issue.  I've also notice that the first couple dozen Mb zip by, but then it hits a wall.

I guess the only way around it is to use a windows vm.. sigh

---

### Post by feedmecmoore on 2009-09-19
Success at last!

[_This thread_]("http://thread.gmane.org/gmane.linux.usb.general/22303") on the linux-usb mailing list has a patch that adds this device to the kernels 'usb quirk' list.  Once that gets upstream, it should work out of the box.

I did some more digging and found [this faq entry]("http://www.linux-usb.org/FAQ.html#i5") that shows how to set the max transfer sectors without recompiling (or rebooting) the kernel.

To make it work, do this (replace sdd with the device of your P7):
```
cat 64 > /sys/block/sdd/device/max_sectors
```I'm now happily transfering at 3MB/s (according to gnome).

---

### Post by xenogia on 2009-09-30
> **feedmecmoore said:**
> Success at last!

[_This thread_]("http://thread.gmane.org/gmane.linux.usb.general/22303") on the linux-usb mailing list has a patch that adds this device to the kernels 'usb quirk' list.  Once that gets upstream, it should work out of the box.

I did some more digging and found [this faq entry]("http://www.linux-usb.org/FAQ.html#i5") that shows how to set the max transfer sectors without recompiling (or rebooting) the kernel.

To make it work, do this (replace sdd with the device of your P7):
```
cat 64 > /sys/block/sdd/device/max_sectors
```I'm now happily transfering at 3MB/s (according to gnome).

Hey feedmecmoore,

Just to let you know the command that actually works for me anyway is

```
echo 64 > sys/block/sdf/device/max_sectors
```
SDF being my iriver p7

---

