---
title: "Dual Booting with Windows 7"
date: 2012-06-12
forum: General Help
---

### Post by aylerni on 2012-06-12
I'm planning on formatting the Linux hard drive&install windows 7, and I need to know why the boot entries are not showing, also why the micro-sd card that worked to bootup livecd with is not working anymore..

Help appreciated

---

### Post by WorMzy on 2012-06-12
What are "the boot entries", and why do they prevent you from formatting your hard drive?

---

### Post by aylerni on 2012-06-12
> **WorMzy said:**
> What are "the boot entries", and why do they prevent you from formatting your hard drive?

The problem is, I'm using Linux as main OS, which mean I cant format the HD without booting in LiveCD (in my ways of thinking).

Boot entries = the OS in grub.cfg

---

### Post by irv on 2012-06-12
You must do things in the right order. If you install Windows 7 it will write over the MBR and your grub will not be seen at boot so you will not be able to boot into Linux. In order to set this up right. One should first install Windows then install Ubuntu last. This will then setup the grub so you can boot into either or. Remember doing it this way, Linux will see the size of your hard drive and divide the disk for both OS's.
There is a way around this if you have Linux already installed, you can install a program call gparted and shrink the Linux partition, install windows in it's own partition, then run the grub repair from a live booted CD, fix the grub to show at boot up so you can boot into either or.
I would do it in the right order this way everything should just work.

---

### Post by WorMzy on 2012-06-12
> You must do things in the right order. If you install Windows 7 it will write over the MBR and your grub will not be seen at boot so you will not be able to boot into Linux. In order to set this up right. One should first install Windows then install Ubuntu last.

I assume that's what OP is doing, hence why they're trying to format their disk. I still don't understand the problem though, grub (and it's configuration) isn't looked at while booting a LiveCD..

---

### Post by irv on 2012-06-12
> **WorMzy said:**
> I assume that's what OP is doing, hence why they're trying to format their disk. I still don't understand the problem though, grub (and it's configuration) isn't looked at while booting a LiveCD..

You are right. All the OP needs to do is install Win7 and not worry about formatting the drive. Windows will take care of that. After that just install Ubuntu and it will setup the drive and install and they will have a Dual booting system with Win7 and Ubuntu.

---

### Post by wilee-nilee on 2012-06-12
OP run in Ubuntu to update the grub.cfg
```
sudo update-grub
```If you want windows without its boot partition, make a ntfs in gparted first with a boot flag and install to it from the windows disc. The boot partition is really only needed if you use the windows encryption.

Really windows should be the first partition on the HD if you only have one, if you ever want to repair it easily.

---

### Post by Kira_Belka on 2012-06-12
Just two ways
1. EasyBCD ( so Win7-bootloader)
2. Ubuntu CD (repairing grub )

I don't see prob)

---

### Post by aylerni on 2012-06-13
Thx for replies, I think I know the situation now XD im noob.. (im trying with ms-sys now)

---

### Post by aylerni on 2012-06-13
Fatal: /dev/sdh1 is not a master device with a primary parition table

I did press "Create partition table" and allocate memory..
Im using USB, anyone can help?

---

### Post by WorMzy on 2012-06-13
To be honest, Iqm still not sure what you're doing here, but in regards ts that error, /dev/sdh1 is a partition on /dev/sdh, which is why it's "not a master device with a primary parition table". Try again with /dev/sdh.

---

