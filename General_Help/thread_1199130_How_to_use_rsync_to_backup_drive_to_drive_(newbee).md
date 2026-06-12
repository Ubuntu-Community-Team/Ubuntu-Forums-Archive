---
title: "How to use rsync to backup drive to drive (newbee)"
date: 2009-06-28
forum: General Help
---

### Post by gilch on 2009-06-28
I have Ubuntu 9.04.
I want to back up one hard drive onto another hard drive using rsync. (I want to use the delete option, but not the compression since both drives are the same size). When I do that, the resulting hard drive should be identical to the original drive I suppose. That's what I want.

Now I don't know how to refer to the two drives.

I have three Hard Drives. When I go 'Places', 'Computer' it lists the three drives by the same name: 'New Volume'. Very confusing.

When I go Filesystem, it lists them as follows:
New Volume
New Volume_ 
New Volume__

Now, if I want to use rsync to backup 'New Volume' to 'New Volume_'
how do I refer to them?

2d question: how to write the rsync command:
I think I would want to use the 'delete' option as well as 'a' and 'w'.  Any other options I should use?

Sorry to be so new...

Gilles

---

### Post by Legace on 2009-06-28
Open Terminal, and post the output of ```
blkid
``` and ```
sudo fdisk -l
```

---

### Post by gilch on 2009-06-28
gilles@gilles-desktop:~$ blkid
/dev/sda1: UUID="f778dc0b-f433-462e-a94f-82d41e024528" TYPE="swap" 
/dev/sda2: UUID="a427db27-33b7-475f-8e76-961c99f96aab" TYPE="ext3" 
/dev/sda3: UUID="678eb2fb-4ef0-42ee-b3aa-0d0940477015" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 
gilles@gilles-desktop:~$ sudo fdisk -l
[sudo] password for gilles: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x181394df

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  82  Linux swap / Solaris
/dev/sda2   *        1217       13374    97659135   83  Linux
/dev/sda3           13375       38913   205142017+  83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5833190b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x947b947b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       16708   134206978+   7  HPFS/NTFS
/dev/sdc2           16709       38913   178361662+   f  W95 Ext'd (LBA)
/dev/sdc5           16709       38913   178361631    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd04e618b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976759808    7  HPFS/NTFS
gilles@gilles-desktop:~$

---

### Post by Legace on 2009-06-28
Which drives do you want to copy (the 320GB one or the 1TB one)?

---

### Post by gilch on 2009-06-28
I want to copy one of the 1TB onto the other 1TB.
Gilles

---

### Post by XCan on 2009-06-28
What do you get if you type df -h? All you need is to find out the mount points for the two drives.

---

### Post by blueridgedog on 2009-06-28
> **gilch said:**
> Now, if I want to use rsync to backup 'New Volume' to 'New Volume_'
how do I refer to them?

2d question: how to write the rsync command:
I think I would want to use the 'delete' option as well as 'a' and 'w'.  Any other options I should use?


You refer to them based on where you have mounted them.  

A simple backup command is:

```
rsync -av /sourcefolder/ /path/to/destination/folder --delete 
```

An example out of my backup is:

```
rsync -av /documents/ /mnt/Backup/Documents --delete --exclude
```

Since you stated that you wanted to copy one of the 1T drives to the other, your Two 1T drives are:

/dev/sdb: 1000.2 GB, 1000204886016 bytes
With only one partition:
/dev/sdb1 1 121602 976759808 7 HPFS/NTFS

and

/dev/sdd: 1000.2 GB, 1000204886016 bytes
With only one partition:
/dev/sdd1 1 121602 976759808 7 HPFS/NTFS

But you did not state from which to which you want to make the copy or where you are mounting them (if you are).  If you are mounting them or they are being auto-mounted, then we need to take over the mounting of them.

But, they don't show up on the blkid...

So to help further I and the others will need the ID of these disks and where they are mounted.

So can you post the output of 

```
blkid /dev/sdb1
```

and

```
blkid /dev/sdd1
```

and 

```
mount
```

Also, please tell us if you can which drive has data and which is the backup target.

---

### Post by gilch on 2009-06-28
There was no output from the blkid commands, but mount has the following:

gilles@gilles-desktop:~$ blkid /dev/sdb1
gilles@gilles-desktop:~$ blkid /dev/sdd1
gilles@gilles-desktop:~$ mount
/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gilles/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gilles)
/dev/sdd1 on /media/New Volume type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1 on /media/New Volume_ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdc5 on /media/New Volume__ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
gilles@gilles-desktop:~$ 

Now to know which one to copy from I don't know. A couple of months ago I used a copy command to write one drive on the other. Now I am really afraid to copy the wrong one. From Filesystem it is the one they call 'New Volume', to be written to 'New Volume_' (with one underline following it). In term of 'sd...' I don't know which is which.

(I did not answer right away because since I put the question I fell and broke my wrist. I am just back from the hospital with a cast...no kidding. I am typing with my right fingers only. Thanks for your efforts to help)

---

### Post by gilch on 2009-06-28
The result of df -h is:

gilles@gilles-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              93G  5.2G   83G   6% /
tmpfs                 977M     0  977M   0% /lib/init/rw
varrun                977M  344K  977M   1% /var/run
varlock               977M     0  977M   0% /var/lock
udev                  977M  184K  977M   1% /dev
tmpfs                 977M  452K  977M   1% /dev/shm
lrm                   977M  2.7M  975M   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sda3             195G  109G   76G  59% /home
/dev/sdd1             932G  786G  146G  85% /media/New Volume
/dev/sdc1             128G   20G  109G  16% /media/disk
/dev/sdb1             932G  695G  237G  75% /media/New Volume_
/dev/sdc5             171G   11G  160G   7% /media/New Volume__
gilles@gilles-desktop:~$ 


OK, that is apparently the solution:
Right now the drive FROM is sdd1
and the drive TO is sdb1. That is right, there is more data on sdd1 than on sdb1. That does not change does it? Those were all named automatically. Do they mount differently when I restart?

---

### Post by gabak on 2009-06-29
grsync is a simple graphical interface using GTK2 for the rsync command line
program. It currently supports only a limited set of the most important rsync
features, but can be used effectively for local directory synchronization

---

### Post by blueridgedog on 2009-06-29
So you want to copy from

/dev/sdd1 932G 786G 146G 85% /media/New Volume

To

/dev/sdb1 932G 695G 237G 75% /media/New Volume_


Before proceeding with the rsync command using /media/New Volume and /media/New Volume_ as the names, I suggest we mount them in new places, calling one files and one backup.  You agree?  If you are interested, I will talk you through it.

Also, use your file browser, nautilus, to look over the two mount points and make certain that you are ready to call the first the master and the second a backup.

---

### Post by gilch on 2009-06-29
I should be safe to use this command?

rsync -av sdd1 sdb1 --delete

Thank you for all respondents. I learned a lot.
I will also check this other program the last correspondent mentioned.
Gilles

---

### Post by XCan on 2009-06-29
I would say you should run

rsync -av /media/New\ Volume /media/New\ Volume_ --delete

However, as blueridgedog pointed out, you really should find more sensible names for your mounted drives. If you want to be sure you could also run rsync through the dry-run (-n) flag, which will not perform any changes, it will just tell you what it would do for a live run.

rsync -av /media/New\ Volume /media/New\ Volume_ --delete -n

---

### Post by gilch on 2009-06-29
I had asked earlier how to rename the drive and someone told me I had to reinstall everything. 

Yes I would really like to have useful names for my drives.

---

### Post by gabak on 2009-06-29
go to computer
then when u see the drives right click on any of them 
then select rename like u do on windows xp
that easy

---

### Post by gilch on 2009-06-29
I tried to rename before, and I tried it just now, it says 'The item cannot be renamed'.

---

### Post by blueridgedog on 2009-06-30
Here is how I would do it.

In the following substitute you user name for USER.

Make two directories for the drives to be mounted to:

```
mkdir /home/USER/files
mkdir /home/USER/backup
```

Unmount the drives from their existing mount points:

```
sudo umount /dev/sdd1
sudo umount /dev/sdb1
```

Your user ID on the system is probably 1000, but it is easy to check:

```
cat /etc/passwd | grep USER
```

If your user ID is anything other than 1000, change it in the mount option below.

Edit /ect/fstab to mount the drives in the new locations

```

gksudo gedit /etc/fstab
```

Add The following two lines:

```
/dev/sdd1 /home/USER/files ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 1
/dev/sdb1 /home/USER/backup ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.UTF-8 0 1
```

Save the file then mount them with the following (you may have to restart to reload /etc/fstab, I do not recall)

```

sudo mount /home/USER/files
sudo mount /home/USER/bacukp
```

Run the backup with:

```
rsync -av /home/USER/files/ /home/USER/backup/ --delete
```

Remember to change USER everywhere you see it and also you can adjust the mount point as you want, but make certain you own the mount point.  If you make a mount point in another part of the system, give yourself ownership with:

```
sudo chown USER:USER /path/to/new/mountpoint
```

Good luck and remember...you may need to remove some items from the backup drive and make certain you have them identified correctly.

---

### Post by gilch on 2009-06-30
Thank you Blurridgedog.
Seems to work, when I ran df -h it listed the drives as files and backup. But when I go to Filesystem/media it doesn't show the drives anymore. Before it listed them as New Volume New Volume_ and New Volume__. In 'Places' it didn't change the names. There are still a lot of things I dont understand... but it will come eventually I hope. Thank you again. I'll try my backup now.

I had doubts about two things. Do I use NTFS or EXT??? Then you had 'locale,1000' in one place and 'locale1000' at another. I chose to use 'locale,1000' in both places. I have no idea which is right.

Gilles

---

### Post by blueridgedog on 2009-06-30
> **gilch said:**
> Thank you Blurridgedog.
Seems to work, when I ran df -h it listed the drives as files and backup. But when I go to Filesystem/media it doesn't show the drives anymore. Before it listed them as New Volume New Volume_ and New Volume__. In 'Places' it didn't change the names. There are still a lot of things I dont understand... but it will come eventually I hope. Thank you again. I'll try my backup now.

I had doubts about two things. Do I use NTFS or EXT??? Then you had 'locale,1000' in one place and 'locale1000' at another. I chose to use 'locale,1000' in both places. I have no idea which is right.

Gilles

I corrected the typo, where a comma was missing.

I will have to think about places, as you really want to remove them rather than change them as they are now under your home directory. 

Also, keep in  mind that the object isn't to copy and paste the commands, but to think about (and gradually grow to understand) the methods and tools at play.

---

### Post by gilch on 2009-06-30
I ran the backup for a Dry run, then ran it for real. It seems to have worked fine. It removed files that had been removed and added new files. I do hope it has replaced modified files as well.

Thanks for your help and advice. I am learning gradually. I don't expect to understand everything right away.
Gilles

---

