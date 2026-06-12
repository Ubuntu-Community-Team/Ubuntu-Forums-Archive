---
title: "Cannot boot after removing partition with GParted"
date: 2009-07-29
forum: General Help
---

### Post by jcobban on 2009-07-29
I removed an unused partition from one of my drives, but now I can no longer boot.  Grub gives me error 22, presumably because it can no longer find the partition I deleted. I have had to boot from an Ubuntu startup CD.  I have tried running grub under that startup CD, but it cannot seem to see my drive configuration.

I have two hard drives on SCSI.  The first one has Windows XP installed on it the second has Ubuntu 9.04.

Starting grub on the Ubuntu startup CD I can issue root (hd0,0), which would point at the Windows drive, but if I try to issue root (hd1,0) to point at the Ubuntu partition I get drive not found.  I issued the find command under grub, but it couldn't find the configuration files, which makes sense since those files are over on (hd1,0), which I cannot issue the root command for.

I am probably failing to understand something about how grub is set up.  Of course I did not install grub, that was done for my by the Ubuntu installation, so I don't know it is currently set up.

---

### Post by approaching on 2009-07-29
It is entirely possible that you did delete your install with gparted, but grub was on the other disk. Here is a scenario where something like this could happen (and has happened to me in the past)

you install on your one drive in your computer
you use that for a while, but get a new drive
so you install the new os using both disks

now one of a few terrible things happen
you nuke the old one with gparted, but you didn't realize that grub was still on it, and you can't boot your new drive

you nuke your new old drive, but you accidentally installed the os on it instead of your new drive, probably because of which wire is put where (ie, you didn't check the disk sizes when you did the install)

or a few other fun combos, the bottom line is, pop in a live disk, see if you have any files on either of the drives, pull them off with an external drive, then NUKE THEM BOTH either in the installer or after you have installed (and make sure that grub is put on the right disk, and not just using the old grub on the old disk)

---

### Post by michy99 on 2009-07-29
Post the output of:```
sudo fdisk -l
```

---

### Post by jcobban on 2009-07-29
> **approaching said:**
> It is entirely possible that you did delete your install with gparted, but grub was on the other disk. Here is a scenario where something like this could happen (and has happened to me in the past)


Thank you.  After playing around I realized that my BIOS was set up to boot from the first drive (the one with Windows XP).  Since Windows does not provide any place where Grub can put its files, those files were over on the second drive, and as a result of the process of installing two copies of Ubuntu on the second drive, the boot record on the first drive was pointing at the second Ubuntu partition, so when I deleted that partition I had to issue:

grub> setup (hd0) (hd1,0)

to reinstall the grub stage 1 on my first drive, but point its stage 2 over at the first partition on my second drive.  Doing a setup of (hd1) had no effect, because the boot record on the second drive is not used.

---

