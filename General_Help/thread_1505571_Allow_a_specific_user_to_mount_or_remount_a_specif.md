---
title: "Allow a specific user to mount or remount a specific partition"
date: 2010-06-09
forum: General Help
---

### Post by jerome1232 on 2010-06-09
Hey, on my system I want user1 and only user1 to be able to mount and unmount a specific partition, this partition contains backups and is usually mounted read only, needs to be temporarily mounted read/write by user1 while doing the backup.

user1 is an unprivileged user. 

I've read that the user option will let any user mount the file-system (and only that user can then subsequently unmount it) and that the users option allows any user to mount or unmount the file-system.

I also found this in mount's man page
> The owner option is similar to the user option, with the restriction that the user must be the owner of the special file. This may be useful e.g. for /dev/fd if a login script makes the console user owner of this device. The group option is similar, with the restriction that the user must be member of the group of the special file.

So it looks like I'd need a login script for that user to make the user owner of the device file (/dev/voiceserv/backup in this case) 

So how can I go about doing that?

---

### Post by dino99 on 2010-06-09
i use mountmanager, if you check about a partition, you can set your pref to the question:

who can mount the partition, choices are into general tab:
- only admin
- concreate user
- everybody

then, in advanced tab, other settings can be made

---

### Post by jerome1232 on 2010-06-09
I forgot to mention this particular system has no gui, so mountmanager wouldn't be an option (it's gui only correct?)

Thanks for the suggestion though.

---

### Post by srs5694 on 2010-06-09
You might look into using udev rules for this. [Here's a wiki entry](http://www.mythtv.org/wiki/Device_Filenames_and_udev) on udev rules, albeit for video device files. You'd do something similar, but instead of creating a symbolic link with a specific name, you'd change the owner of the device. You may be able to find better examples of udev rules for this sort of thing by Googling (I just happened to know about the one to which I linked). Using udev rules, however, will leave the device permanently owned by the user in question.

Another option is to mount the device read/write on a regular basis, but ensure that only user1 has write access to its files by adjusting the ownership and permissions on the mount point (after it's mounted) and its subdirectories. This is probably a simpler approach, and it's more of a standard way of doing things; but there might be more of a chance of things going wrong -- say, if the permissions were accidentally changed, everybody might then be able to write to the partition.

---

### Post by Morbius1 on 2010-06-09
You could use bindfs to do what you want: There's a bindfs howto here: [http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

I have a data partition at sdb6:

The first thing I'm going to do is create a hidden mount point and then a non-hidden directory to bind to that mountpoint:
```
sudo mkdir /.DATA
sudo mkdir /DATA

```Now I add the following in fstab to mount /sdb6 to the hidden mountpoint: /.DATA
```
/dev/sdb6 /.DATA ext3 defaults 0 2
```By default that will mount sdb6 to /.DATA with owner = root with r/w access only to root.

I now add another line to fstab:
```
bindfs#/.DATA /DATA fuse perms=0755,mirror=user1 0 0
```To user1 the /DATA directory ( the non-hidden directory ) and everything in it is owned by him ( mirror=user1 ) with r/w access to him alone ( perms=0755 ). To everyone else it's still owned by root but with read only access.

Anyway, something to consider.

---

### Post by jerome1232 on 2010-06-11
Changing permissions of the files wouldn't be an option since the partition contains rsync'd backups, which have preserved permissions that will be whatever the original files permissions were.


I'm taking a look at udev rules and bindfs right now to see which one I'll try. Will post back with what works for me.

edit:I don't think bindfs will do what I want actually, I think udev it is.

---

### Post by jerome1232 on 2010-06-16
So I think I need some help with the udev rules.

I made an attempt at it but it doesn't seem to be working.

I was following through with this write up [http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

this is the device I want to change
```
P: /devices/virtual/block/dm-5
N: mapper/voiceserv-backup
L: -100
W: 73
S: block/251:5
S: dm-5
S: disk/by-id/dm-name-voiceserv-backup
S: disk/by-id/dm-uuid-LVM-qpmezuijY6T06z0qPFivjOgNZD32ipBUDkshxZeX3Pum8JlZQsU73Ae24nmVcOTD
S: disk/by-uuid/62363f74-ecce-4731-aa1a-bb5e067becf4
S: voiceserv/backup
E: UDEV_LOG=3
E: DEVPATH=/devices/virtual/block/dm-5
E: MAJOR=251
E: MINOR=5
E: DEVNAME=/dev/mapper/voiceserv-backup
E: DEVTYPE=disk
E: SUBSYSTEM=block
E: DM_NAME=voiceserv-backup
E: DM_UUID=LVM-qpmezuijY6T06z0qPFivjOgNZD32ipBUDkshxZeX3Pum8JlZQsU73Ae24nmVcOTD
E: DM_SUSPENDED=0
E: DM_UDEV_RULES=1
E: DM_VG_NAME=voiceserv
E: DM_LV_NAME=backup
E: DEVLINKS=/dev/block/251:5 /dev/dm-5 /dev/disk/by-id/dm-name-voiceserv-backup /dev/disk/by-id/dm-uuid-LVM-qpmezuijY6T06z0qPFivjOgNZD32ipBUDkshxZeX3Pum8JlZQsU73Ae24nmVcOTD /dev/disk/by-uuid/62363f74-ecce-4731-aa1a-bb5e067becf4 /dev/voiceserv/backup
E: ID_FS_UUID=62363f74-ecce-4731-aa1a-bb5e067becf4
E: ID_FS_UUID_ENC=62363f74-ecce-4731-aa1a-bb5e067becf4
E: ID_FS_VERSION=1.0
E: ID_FS_TYPE=ext4
E: ID_FS_USAGE=filesystem
E: FSTAB_NAME=/dev/mapper/voiceserv-backup
E: FSTAB_DIR=/backup
E: FSTAB_TYPE=ext4
E: FSTAB_OPTS=defaults,nodev,nosuid,owner,ro
E: FSTAB_FREQ=0
E: FSTAB_PASSNO=2

```

I wrote this rule in /etc/udev/rules.d/10-local.rules

```
SUBSYSTEM=="BLOCK" , KERNEL=="dm-5" , GROUP="backups"
```

But on a reboot the device is not remountable as rw by my user in that group. The device also seems to still have root:disk ownership instead of root:backups as I expected.

---

### Post by srs5694 on 2010-06-16
It's conceivable that your udev rules are being overwritten by a later udev rule. My knowledge of the sequence in which udev applies its rules on an Ubuntu system is limited, though, so I'm afraid I can't be more specific; I'm just speculating.

This strikes me as the sort of thing for which there's got to be a more elegant solution, but I can't think of one. I know that Samba provides options to permit this sort of control on Samba shares, but I don't know of any relevant mount options, offhand. Maybe perusing the "mount" man page would provide some ideas....

---

