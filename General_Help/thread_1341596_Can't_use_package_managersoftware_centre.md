---
title: "Can't use package manager/software centre"
date: 2009-11-29
forum: General Help
---

### Post by Pan_Synaptic on 2009-11-29
Right then, my main Ubuntu installation failed recently but managed to back up all my files from my XP partition so wasn't a huge disaster.

I've reinstalled 9.10 and it's been working fine tonight, got Pidgin and VLC installed again etc. However when playing Quake live the whole machine froze and needed to be reset. First of all the hard drive was missing from the bios and then i noticed the power cable was slightly loose (oops)

Now it's booted up but when i open the synaptic package manager i get this
```
E: Unable to write mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I've searched round and most places say there's not enough hard drive space, however this is a new installation on a 500gb drive.

```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e5472

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60050   482351593+  83  Linux
/dev/sda2           60051       60801     6032407+   5  Extended
/dev/sda5           60051       60801     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
16 heads, 63 sectors/track, 1453521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x0d3f39b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1     1453517   732572536+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x42974296

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001fcac

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      182401  1465136001   83  Linux

user@user-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             453G  3.3G  427G   1% /
udev                 1007M  300K 1006M   1% /dev
none                 1007M  312K 1006M   1% /dev/shm
none                 1007M   84K 1007M   1% /var/run
none                 1007M     0 1007M   0% /var/lock
none                 1007M     0 1007M   0% /lib/init/rw
```

It won't let me get anything through the terminal either
```
sudo apt-get install -f
[sudo] password for user: 
Reading package lists... Error!
E: Unable to write mmap - msync (5: Input/output error)
E: The package lists or status file could not be parsed or opened.

```

The update manager is giving the same error message as well.

I've been using Ubuntu for a while but i'm still a n00b so please explain things slowly and clearly ;)

ANY help is appreciated, can't install anything at the moment which is a bit of a pain on a very fresh installation

---

### Post by raktarok on 2009-11-29
Try this:
```
sudo apt-get autoclean
sudo apt-get update
```
Then see if you can install packages.
But I don't know if this will help....

---

### Post by raktarok on 2009-11-29
Okay, I did a bit of a research on the error, and this looks like a problem with filesystem. So on your next boot, try checking the filesystem. Do this from a terminal to force the check and then reboot. 
```
sudo touch /forcefsck
```
fsck should run at boot time now, and it should show you the filesystem problems, if any.

---

### Post by Pan_Synaptic on 2009-11-30
And just like that the package managers are working fine again. Except i didn't do anything except leave the computer on XP for a while (which i did yesterday anyway while ubuntu was playing up)

I'm starting to think that the hard drive might be on it's way out really

Thanks for the advice though, if it happens again (i booted up ubuntu to try the above and when i opened the package manager it's working, only been working for a few minutes so not saying it's 100% fixed lol) i'll give it ago then

---

