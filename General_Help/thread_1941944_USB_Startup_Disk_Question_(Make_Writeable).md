---
title: "USB Startup Disk Question (Make Writeable?)"
date: 2012-03-16
forum: General Help
---

### Post by pyrotherm on 2012-03-16
Hi all,

Have a question:

I created a USB Startup Disk with Ubuntu 10.04.3LTS on it, and when I insert it into my Ubuntu 10.04.3LTS machine, I can't write to it.

It always mounts as read-only by default.

Is there a way to change this behavior, so that I may place files on the drive?

I checked the flags in GParted, they are "boot" & "lba".

---

### Post by ajgreeny on 2012-03-16
If you mean you can't write to it when you have booted to it, you need to create it again using either unetbootin or the ubuntu  startup-disk-creator and make sure that you choose persistemce. The option to enable that is at the bottom of the creator window.  You should be able to write to it if you simply plug it in to a running OS, though it will have many files already on it.

There may even be a way to add the necessary file (casper.rw) to your disk without re-creating it, but I am not aware of how you can do that.

Worth a search, but it only takes a few minutes to run the startup-disk-creator, so may not be worth the hassle.

---

### Post by Rebelli0us on 2012-03-16
Is it a flash drive? Maybe you accidentally flipped the write-protect tab.

---

### Post by pyrotherm on 2012-03-17
@ajgreeny

It's not an issue with writing to it from WITHIN the live environment, it's when i try to write files/folders to the flash drive from a regular install.

Basically, I want to be able to use the drive as both a live disk, and a storage device for my linux/windows PCs

---

### Post by ajgreeny on 2012-03-17
Is there any free space on the disk to write to?
Perhaps you made a persistent live OS and filled the available disk space.

With the flash stick attached and mounted, which it probably will by itself, run the command ```
df -h
```and look for the line of output related to that flash drive.  I get
```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    9.9G  4.9G  4.6G  52% /
none      devtmpfs   1002M  276K 1002M   1% /dev
none         tmpfs   1007M  3.3M 1004M   1% /dev/shm
none         tmpfs   1007M   92K 1007M   1% /var/run
none         tmpfs   1007M     0 1007M   0% /var/lock
none         tmpfs   1007M     0 1007M   0% /lib/init/rw
/dev/sda2     ext4    139G  107G   25G  82% /home
[COLOR=Red]/dev/sdc1     vfat     15G  1.8G   13G  13% /media/KINGSTON[/COLOR]
```The line in red is my live system with Lubuntu 12.04 beta.  As you see 13% of the 15GB is used.

---

