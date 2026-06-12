---
title: "How do I Share a RAID Array"
date: 2010-02-06
forum: General Help
---

### Post by salgiambruno on 2010-02-06
I'm an absolute NEWBIE, so please pardon my disorientation . . .

I have recently installed Ubuntu 9.10 Desktop on an old P4 system, have installed Samba and successfully configured SMB.CONF to share a folder "/SRV/SAMBA/SHARE."

I am now trying to set up a local RAID5 volume (3ware 7500) for sharing on the local network.  My goal is to use this RAID volume as the central repository for media files for users on the network.  I would like it to mount at the server automatically (I currently have to mount manually and provide a password), and I would like for it to be mapped automatically as a drive whenever I log onto the server from a networked device (i.e. another computer).

I have tried to set up a SHARE for this RAID volume in SMB.CONF, but I think I am not getting the path correct.  How do I specify the path to a RAID volume (it's showing up as RAID ARRAY) located on my desktop?  When I open properties for the volume using Nautilus, the location shows up as "media" and the volume reads "RAID ARRAY."  When I pull up properties directly from the icon on the desktop, location is "on the desktop" and volume is "RAID ARRAY."

I have the following settings:

[RAID ON UBUNTU]

comment - Ubuntu RAID ARRAY Share
path = /media/RAID ARRAY
browseable = yes
guest ok =yes
read only = no
create mask = 775
directory mask = 0775

I also ran chown nobody.nogroup /media/

Also, but not directly related, I'd like to resolve how to WRITE to another share when logged in at the server.  Permissions on this particular share are set to nobody.nogroup as per the example I was following.  I am able to create/read folders and documents in this particular share from a networked PC, but have only read access from the server itself.

---

### Post by jken146 on 2010-02-07
> path = /media/RAID ARRAY
should be ```
path = /media/RAID\ ARRAY
```
You need to escape the space.

For more Samba help see [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

As for mounting it automatically (on the server), what do you get from ```
$ sudo fdisk -l
```?

---

### Post by salgiambruno on 2010-02-07
thanks jken146... i had a sneaking suspicion that the volume name might be giving me problems since when I did a sudo on it it parsed RAID and ARRAY into two different chunks . . .

however, before i even got your reply, i formatted the volume as an EXT3/4 (it was NTFS) and from thereon out I was able to share it through the Properties tab on the GUI . . . very simple indeed and works like a charm.

your help is MUCH APPRECIATED! :)

---

### Post by salgiambruno on 2010-02-07
jken,

sda is the OS, sdb is the RAID Array . . .

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x64e9e46d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4309    34612011   83  Linux
/dev/sda2            4310        4500     1534207+   5  Extended
/dev/sda5            4310        4500     1534176   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000213577728 bytes
255 heads, 63 sectors/track, 121602 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c0774c2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976768033+   7  HPFS/NTFS


I guess my other question would be, where was the information creating the share posted to?  In Windows, that would be the Registry, but I haven't a clue how Linux accomplishes this, and it would be nice to know so that I will know what to tweak in the future . . .

---

### Post by jken146 on 2010-02-07
I think it goes in /etc/smb.conf

---

### Post by salgiambruno on 2010-02-14
Well, I have opted to forego the software RAID route and instead use the 3Ware controller I have since it provides hardware RAID and has the physical connectors (4) for the drives I need to attach.

From what I've read, Ubuntu provides native support -- and this is showing to be true, since I am able to see my RAID volume using the graphical Disk Managment Utility "Palimpsest" and have been starting and mounting the array manually using said utility.

However, as it stands, I have to start and mount the array each time I boot my server, and since I don't keep my server on all the time, I would like to know if there is a way to start and mount the array automatically, at boot time.

I've read that 3Ware has a CLI (Command Line Utility) for Linux, but don't have a clue as to how I would install it, which version I need, or even if it is supported under Ubuntu Desktop 9.10, or whether using it I can configure my system to auto start and mount the array.

I feel so helpless - the learning curve is steep!  Any suggestions?

---

### Post by jken146 on 2010-02-14
So you want to mount the partition sdb1 at boot?  You need to create a mount point for it and add an entry to /etc/fstab.
```

sudo umount /dev/sdb1 && sudo mkdir /mnt/foo && sudo echo '/dev/sdb1 /mnt/foo ntfs defaults 0 0' >> /etc/fstab && sudo mount -a

```

Change /mnt/foo (both occurrences) to wherever you want the mount point to be. It can be anywhere you like, but a directory within either /mnt or /media is usual.

===================

So those were the instructions; now a bit of explanation.

Linux sees your RAID array as one device, in the same way as it does a single hard disk.  You used **fdisk -l** to list the disks that are present and the partitions on them.  As you can see from the output you pasted above, /dev/sdb1 is the file that represents the single partition on your array.  You can also see that it's formatted with the NTFS file system.

In order to read the files on a partition, Linux needs to mount it somewhere.  To do this:

1. Create a directory ```
mkdir /mnt/foo
```

2. Mount the partition there ```
mount /dev/sdb1 /mnt/foo

To unmount the partition, you would do [code]umount /dev/sdb1
```

Linux keeps a list of the filesystems/partitions it mounts automatically in the file /etc/fstab and in the command above I instruct you to add a line to it. That's the **echo '/dev/sdb1 /mnt/foo ntfs defaults 0 0' >> /etc/fstab** part.  You can edit fstab directly with the command ```
sudo nano /etc/fstab
```  Replace **nano** with any text editor you like, e.g. **gedit**

The last part of the command is **mount -a** -- all this does is tell the computer to mount everything in fstab.

I hope that all makes sense!

---

