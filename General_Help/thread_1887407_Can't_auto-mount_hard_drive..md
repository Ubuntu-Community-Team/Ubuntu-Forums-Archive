---
title: "Can't auto-mount hard drive."
date: 2011-11-27
forum: General Help
---

### Post by Beckenor on 2011-11-27
I dual-boot Windows Vista and Ubuntu 10.04 (Lucid) on my HP G60. I can access all of the files on the part of my hard drive with all of my Vista stuff (Ubuntu calls it 197 GB Filesystem and it is listed right underneath Computer in Places) but it will not stay mounted when I restart Ubuntu. This is annoying because my shortcuts to files on this part and my wallpaper disappear every time I restart my computer. I have already tried using Storage Device Manager. It does what I want, but it can't detect the right filesystem. I want this 197 GB Filesystem to mount automatically every time I start Ubuntu.

---

### Post by hwttdz on 2011-11-27
I think what you're going to want to do is add that drive to your fstab.  

The best way of doing so is to use the uuid of the partition/drive, so I'd start up gparted or something and select the drive of interest and go to properties or somesuch and get the UUID.

Then go to /etc and back up your fstab. 

Then back up your fstab via email. 

Then backup your fstab on external media like a cd.

Then add a line for the drive of the format:
```
UUID=uuidstuffgoeshere  /path/to/mountpoint  filesystemtype  mountoptions          dumpflag fsckorder
```

the uuidstuffgoeshere is obviously just the uuid of the drive which you can get from gparted or /dev/disks/by-uuid/.

/path/to/mountpoint is just where on the filesystem you want the drive to show up.

filesystemtype would be ext3 or ext4 or some other weirder thing if you happen to be like that.

mountoptions are described in detail in the man page for mount, I would guess you don't want block device things, so that would be nodev.  I'd also guess that relatime is fine (I think this may even be the default now), you can also check out pysdm and use the assistant to find some of the flags, I'd recommend checking by hand as I've found it to be buggy, but I haven't used it in a while.

dumpflag is if you want the filesystem to be included in dumps, if you don't backup via dump, just leave it at 0.

And fsck checks, I'd recommend putting it at one more than the current highest number you see in that column.  That way it will get checked occasionally.

After adding to your fstab, just reboot and it will be mounted at /path/to/mountpoint.  Easy peasy.  Just be careful.

Hope that helps.

---

### Post by Beckenor on 2011-11-27
Okay, I'm pretty new to Ubuntu, and LInux in general, and that just went *way* over my head. Could you explain it a little more simply?

---

### Post by fdrake on 2011-11-27
can you post the output for:
```

sudo fdisk -l
less /etc/fstab
blkid

```

---

### Post by Beckenor on 2011-11-27
Like this?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc   proc    defaults        0       0
#Entry for /dev/sda5 :
UUID=52927a5b-88d4-455f-9cbf-d3182b8e94d7       /       ext4    errors=remount-ro       0       1
#Entry for /dev/sda1 :
UUID=3456849C5684608A   /media/3456849C5684608A ntfs-3g defaults,nosuid,nodev,locale=en_US.utf8 0       0
#Entry for /dev/sda3 :
UUID=F8F290E6F290AA80   /media/sda3     ntfs-3g defaults,locale=en_US.utf8      0       0
#Entry for /dev/sda6 :
UUID=bb7f520b-1ee5-45ad-abc1-b6fa67fbf4af       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto,exec,utf8   0       0


~
~

```

---

### Post by fdrake on 2011-11-27
under type are you sure "ntfs-3g" is correct. iF not you may want to try "fuseblk" i am not sure but the mount command describes my ntfs partition as this kind of format.

---

### Post by Beckenor on 2011-11-27
I'm not sure about anything. I have no idea what all of that means. It looks like gibberish to me.

---

### Post by Beckenor on 2011-11-28
Consider this problem fixed. I had my uncle (who is a programmer) walk me through the steps that fdrake and hwttdz suggested. Now Ubuntu works like a charm. Thanks for all the help! :D

---

