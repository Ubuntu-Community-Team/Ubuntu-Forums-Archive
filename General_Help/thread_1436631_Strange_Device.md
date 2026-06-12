---
title: "Strange Device"
date: 2010-03-22
forum: General Help
---

### Post by ScarletWyvern on 2010-03-22
Output of "ls /dev/sd*" prints the following:

```
/dev/sda  /dev/sda1  /dev/sda3  /dev/sda4  /dev/sda5  /dev/sda6  /dev/sdb
```The sda device is, of course, my hard drive; however I can't figure out what that sdb is. Running fdisk only gives me information on sda, and I don't have an external drive of any kind connected. Running "fdisk /dev/sdb" gives me an "Unable to open /dev/sdb" message.

Sdb is there every boot now, but I don't think it was always there... I only noticed it a few weeks ago. I figured, "Eh, it's not causing any problems, so I won't bother it." But now, not knowing what it is is driving me crazy.

Also of note is that dmesg says:
```
[    6.844298] sd 4:0:0:0: [sdb] Attached SCSI removable disk
```I'm not all that familiar with hardware, so I'm not entirely sure what "SCSI removable disk" means, but I know that /dev/sdb is there even when I have nothing connected to my laptop.

Anyone have some insight? Thanks!

---

### Post by darolu on 2010-03-22
"SCSI removable disk" usually refers to a pendrive, did you unmount the last pendrive you used? any memory card (i.e. sd) attached?

It is weird because your /dev/ list is generated everytime you boot; another possibility is a backup application that you may have installed.

---

### Post by ScarletWyvern on 2010-03-22
Well, I don't use any backup application that I'm aware of. What's also strange is that I can't even see the device in something like gParted.

It's like the device is there, but the system is pretending it doesn't exist.

If I plug in some kind of external drive, it of course pops up as sdc.

Generally, I unmount my drives, but if I pulled it out without unmounting, would it really cause something this weird? As I said, sdb is there every single boot, even if I have NOTHING connected to my computer externally.

---

### Post by darolu on 2010-03-23
Yes it is really weird, the not-unmounting thing is the only thing that came to my mind but it shouldn't make it appear even after rebooting.

It's probably a storage device in your laptop that the manufacturer put there for recovery functionality or similar; have you tried to mount it?

```
$ sudo mkdir /media/device
$ sudo mount /dev/sdb /media/device
```

---

### Post by rnerwein on 2010-03-23
hi
/dev/sdb and ( if present ) /dev/sdc are the major devices. when the system boots up there is a "attach" to see if there is a device present where the driver module listen. who else should the system tell when
a "removeable" is pluged in on the fly.
therefor those devices are present even when nothing is pluged in.
ciao

---

### Post by ScarletWyvern on 2010-03-23
> **darolu said:**
> Yes it is really weird, the not-unmounting thing is the only thing that came to my mind but it shouldn't make it appear even after rebooting.

It's probably a storage device in your laptop that the manufacturer put there for recovery functionality or similar; have you tried to mount it?

```
$ sudo mkdir /media/device
$ sudo mount /dev/sdb /media/device
```

I forgot to mention that, actually.

Curiously, trying to mount the device leads to about 20-30 seconds of nothing, and then the shell will spit out "mount: /dev/sdb: uknown device".

I should also mention that the only sort of recovery that HP put on this laptop was a partition on sda. At least, to my knowledge.

> **rnerwein said:**
> hi
/dev/sdb and ( if present ) /dev/sdc are the major devices. when the system boots up there is a "attach" to see if there is a device present where the driver module listen. who else should the system tell when
a "removeable" is pluged in on the fly.
therefor those devices are present even when nothing is pluged in.
ciao

After reading a bit, "sd" is the nomenclature for the SCSI storage driver, right? So, sda being the first hard drive in my computer make sense.

If I understand, what you're saying, sdb is acting as a place-holder of sorts for some removable device? What confuses me about that is if I plug some kind of device in, it will register as /dev/sdc, not sdb.

---

### Post by rnerwein on 2010-03-24
hi
i am confused - those are my entries:
/var/log/messages
tschang kernel: [    7.587365] sd 10:0:0:0: [sdb] Attached SCSI 
tschang kernel: [    8.368968] sd 11:0:0:0: [sdc] Attached SCSI
mount
/dev/sdb on /media/USB_2GB type vfat (rw .......

???? sorry i have no more explanations
ciao

---

### Post by ScarletWyvern on 2010-03-24
Bump.

I just unplugged the receiver for my wireless mouse, my USB keyboard, and even my power cord, and I did a reboot for a clean, controlled test.

/var/log/messages
```
Mar 24 15:40:34 Ciel kernel: [    6.848429] sd 4:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by plughead on 2010-03-24
Do you have a card reader (sd/mmc, micro-sd, pro duo, compact flash, etc.) built-in to your laptop?  If so, that's what you're seeing--they show up even if there's nothing plugged in to them.  (I've got a multi-card reader in my desktop and it shows as sdf-sdj, without a single card plugged in.)  

Try plugging a card in and you should see /dev/sdb1, etc...

---

### Post by ScarletWyvern on 2010-03-24
That's it, plughead. Mystery solved. Thanks!

I never would have thought of the card reader. In fact, I completely forgot I had one until you mentioned it.

---

