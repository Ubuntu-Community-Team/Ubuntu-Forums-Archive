---
title: "Attempting Format of Slave Drive"
date: 2010-06-01
forum: General Help
---

### Post by Jerzeyfbabii on 2010-06-01
Hey everyone,

Having an issue here. I have a hard drive I use as a slave that is running Windows. My laptop is running XUbuntu. I hook it up and attempt to format it using GParted. When I open GParted it says 'Failed to Mount 12gb volume"

I know the hard drive has a password to log in but since it doesn't want to run and has the "disk read error" I just want to format and install Linux on it. So maybe that's what's stopping me, and I don't know how to find a way to type in the password. 

I've also attempted to just install Linux on it but it gets stuck at the same place. What in freaks' name do I do cuz I'm getting a migraine!!!!

-Liz

---

### Post by silkworm2.5 on 2010-06-01
How is the password on it? Within windows? or some other way? you should probably disable the password if it's not made by windows.

---

### Post by dabl on 2010-06-01
Easiest method (and also a potentially destructive one) is the "dd" command.  You can't make any mistake here -- if you want to be super-safe, you can disconnect the main hard drive and leave only your selected victim connected, and do this from a Live CD session.  The "dd" command below will zero out the master boot record, and leave it ready for a new partition table and filesystem. All data on the target drive will be destroyed in this process:

1. In a terminal, identify the device number of your target hard drive, using ```
sudo fdisk -lu

```
2. Let's say it is /dev/sd_b_.  Again in the terminal

```
sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

don't touch anything until the command is finished.  Then, you can boot a GParted Live CD, or any Linux OS that has GParted, and partition the drive.  When it asks you to choose a new partition table type, choose "MS-DOS", and then you can choose a filesystem and let it format (I assume you intend it to be a single partition).

Make sure you use the /dev/sd_x_ number of YOUR target drive. 

Reference:

[http://kubuntuforums.net/forums/index.php?topic=3090824.0](http://kubuntuforums.net/forums/index.php?topic=3090824.0)

---

### Post by Jerzeyfbabii on 2010-06-01
[SIZE=4]Hey there,

Well I finally got it formatted. I figured out GParted while waiting for replies. Now when I go to install the OS it'll say "The ext4 file system creation in partition #1 of /dev/sda failed." 

I've tried re-formatting and setting up ext2, ext4, and even a fat32 partition but continue with the same error. I'm gonna need Rogaine for women after this if I don't figure this crapola out. Help? :mad:[/SIZE]

---

### Post by dabl on 2010-06-03
Well, you apparently DIDN'T get it formatted ... :cry: 

There _may_ be a hardware problem on that hard disk drive, but you won't know for sure until you "dd" it, as indicated above.  If, after you "dd" it, and then set a new partition table, and format it, it still pukes up a "filesystem creation error", you'll know you have a piece of dumpster food on your hands -- probably a media defect in the MBR area.  Good luck!

---

