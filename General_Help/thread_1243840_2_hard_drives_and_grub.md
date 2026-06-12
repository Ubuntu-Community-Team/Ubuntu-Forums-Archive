---
title: "2 hard drives and grub"
date: 2009-08-18
forum: General Help
---

### Post by Sin@Sin-Sacrifice on 2009-08-18
Not sure where to put this but I just snatched my old hdd from my mom's comp because I had a LOT of time in it and well... slapped it into my new pc and I don't see it in grub. I found a few sites talking about some stuff I don't quite understand with editing menu.lst but nothing specific to my needs. I just want to boot the old 8.04 and backtrack partitions on the other hdd. Anyone? Pre-Thank You...

---

### Post by bodhi.zazen on 2009-08-18
It has to do with which drive is master and which is slave and on the BIOS.

Some BIOS allow you to select which drive to boot from.

Otherwise, switch the position of your hard drives.

If that fails you may need to re-install GRUB.

[Recovering Ubuntu after installing Windows - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Sin@Sin-Sacrifice on 2009-08-18
How do I change whether its master or slave when its a sata drive? They're set as master 1 and master 2. I've tried everything I can think of to bring up a boot menu for the mobo and nothing is working. It's not displayed. Could I just switch sata cables? I don't really want to do that every time so is there a way around it if that's what I have to do?

---

### Post by VMC on 2009-08-18
Maybe I'm reading this wrong, but grub doesn't know the second drive. If your getting a grub menu then its working. You have to edit your grub menu.lst file for it to "see" the partitions on the new drive. Grub should be on your sda1 or first hard drive, and sda2 should be your second drive.

When you turn on your pc, do you get a grub menu?

---

### Post by Sin@Sin-Sacrifice on 2009-08-18
Yeah I do... It has the 9.04 and XP Pro 64 from hd1 and nothing from hd2. I did some changes to menu.lst but it didn't recognize (hd1,0) or 1. I'm going to read the how-to in your signature and see what I can learn.

P.S. Sorry I take so long... my wireless connection always times out in ubuntu so rebooting into windows every 20 min or so.

---

### Post by bodhi.zazen on 2009-08-18
If you have grub installed you need to edit /boot/grub/menu.lst

assuming Ubuntu is on the second hard drive, it should look something like :

```
Title Ubuntu9.04
root (hd1,0)
kernel /boot/vmlinux.xxx-yyy.zzz bla bla
initrd  /boot/initrd-xxx.zzz
```

The important part is to get the "root (hd1,0)" correct and to mark at least one partition on the second hard drive as bootable.

Can you boot the desktop CD and from there confirm your partitions and post the relevant parts of /boot/grub/menu.lst ?

---

### Post by Sin@Sin-Sacrifice on 2009-08-19
I figured it out... I just copied the entries in menu.lst on the old drive and changed the hdx. Working now... just have to fix the drivers.

---

### Post by bodhi.zazen on 2009-08-19
w00t !!!

---

