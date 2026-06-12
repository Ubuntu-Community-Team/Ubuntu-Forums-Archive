---
title: "Panic - Cannot Mount Partition"
date: 2011-06-29
forum: General Help
---

### Post by Quarkrad on 2011-06-29
Help - cannot mount media/sda5, wife's 10.10 machine, this partition has all her user files on!  When I switch on this volume is not mounted under nautilus.  In nautilus the partiton use to read **HomeFiles**  now it reads **sda5** (which it physically is).  If I right click and choose Mount I get the message


Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I get the same message if I try to mount sda5 using System/Admin/Disk Utility.

This morning I made a change and probably messed something up.  There was a short cut to a folder on this partition in the top panel that stopped working. I right clicked on Permissions and reset the location, following the screens I selected /media/sda5/name of folder.  It worked when I did it this morning but not now after a re boot.  How can I mount sda5?  I need to rename it back to HomeFiles.

---

### Post by dino99 on 2011-06-29
its time to run fsck on it

---

### Post by Quarkrad on 2011-06-29
Sorry - forgot to say I'm a newbie.  So not sure what commands to use - assume you run fsck from terminal.  The partition is ext4 and when in System/Admin/disk Utility and got the error message on trying ti mount I did run the Check Filesystem option.  It can back and said the 'file system is clean'.

---

### Post by seawolf167 on 2011-06-29
For an ext4 partition, the *fsck* command would be

```
fsck -F ext4 -y /dev/sda5
```

---

### Post by Quarkrad on 2011-06-29
I ran the command and was asked to put in another parameter.  This is the output:

[B]liz@lizubuntu:~$ fsck -F ext4 -y /dev/sda5
fsck from util-linux-ng 2.17.2
Usage: fsck.ext4 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
liz@lizubuntu:~$ fsck -F ext4 -y /dev/sda5 -p
fsck from util-linux-ng 2.17.2
e2fsck: Only one of the options -p/-a, -n or -y may be specified.
liz@lizubuntu:~$ fsck -F ext4 -y /dev/sda5 -y
fsck from util-linux-ng 2.17.2
Usage: fsck.ext4 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
		[-I inode_buffer_blocks] [-P process_inode_size]
		[-l|-L bad_blocks_file] [-C fd] [-j external_journal]
		[-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
liz@lizubuntu:~$ [/B]


I rebooted and got the message - Press S to skip mounting or M for manual recovery.  I tried M and eventually got another message
[B]
Ext4-fs (sda5) Unrecognized mount option "grid=1000" or missing value[/B]

I rebooted, this time pressing the S option and got to Desktop.  Nautilus now shows (under Places) both HomeFiles and sda5 - neither are mounted, or can be mounted.  Thanks for your help.

---

### Post by seawolf167 on 2011-06-29
Sorry, replace the -F with a -t (for type) which is followed by ext4

```
sudo fsck -t ext4 -y /dev/sda5
```

Remember that the partition needs to be unmounted to run *fsck*

---

### Post by Quarkrad on 2011-06-29
The output to your command was

[B]liz@lizubuntu:~$ sudo fsck -t ext4 -y /dev/sda5
[sudo] password for liz: 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
HomeFiles: clean, 12455/1117920 files, 2243872/4466062 blocks
liz@lizubuntu:~$ [/B]

however, machine still boots with press S and M before Desktop, HomeFiles and sda5 (which are the same thing) are still not mounted and cannot be mounted.

Out of interest my fstab looks like

[B]UUID=edad6a75-8cff-495b-95f9-d67037bb660a / ext4 defaults 0 1
UUID=EE80115F80113017 /media/WINXP ntfs-3g defaults 0 0
UUID=ae207b6d-9c06-4865-b0a4-4f3f16f60e25 /media/sda5 ext4 user,gid=1000,uid=1000 0 0
UUID=7726AB6749D7F693 /media/HFCopy ntfs-3g defaults 0 0
UUID=e928983b-2bc5-4b95-b692-a3999f2c217e swap swap sw 0 0
UUID=10144AE6144ACE82 /media/Images ntfs-3g defaults 0 0
UUID=E65C87295C86F399 /media/Backup ntfs-3g defaults 0 0[/B]

As a newbie I do not know what I'm talking about here but I do note that most of the partition have **defaults 0 0** at the end.  sda5 is very different.  Should it not read

UUID=ae207b6d-9c06-4865-b0a4-4f3f16f60e25 /media/HomeFiles ext4 defaults 0 0

---

### Post by seawolf167 on 2011-06-29
> **Quarkrad said:**
> 
As a newbie I do not know what I'm talking about here but I do note that most of the partition have **defaults 0 0** at the end.  sda5 is very different.  Should it not read

UUID=ae207b6d-9c06-4865-b0a4-4f3f16f60e25 /media/HomeFiles ext4 defaults 0 0

No - the values are [dump] [fsck order], so a 1 just says what order to check it in (a 0 means to ignore it), so you can leave it.

What is the output of the command

```
mount
```

---

### Post by Quarkrad on 2011-06-29
liz@lizubuntu:~$ mount
/dev/sda1 on / type ext4 (rw,commit=0)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda2 on /media/WINXP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/HFCopy type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb5 on /media/Images type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb6 on /media/Backup type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/liz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=liz)
liz@lizubuntu:~$

---

### Post by seawolf167 on 2011-06-29
What errors do you get from the following commands?

```
sudo umount /dev/sda5
sudo mkdir /media/homefiles
sudo mount /dev/sda5 /media/homefiles
```

---

### Post by Quarkrad on 2011-06-29
OK - this was the output

[B]liz@lizubuntu:~$ sudo umount /dev/sda5
[sudo] password for liz: 
umount: /dev/sda5: not mounted
liz@lizubuntu:~$ sudo mkdir /media/homefiles
liz@lizubuntu:~$ sudo mount /dev/sda5 /media/homefiles
liz@lizubuntu:~$ [/B]

I went into nautilus and HomeFiles was mounted and I could see/access the files. I rebooted and got this message

[B]An error occured while mounting /media/sda5

Press S to skip mounting or M for manual recovery[/B]

Homefiles and sda5 are still showing in nautilus and cannot be mounted.

---

### Post by seawolf167 on 2011-06-29
Please post the output of

```
sudo blkid
```

we're going to remove the current /etc/fstab entry and add a new one since it mounted with no problems but wouldn't automount

---

### Post by Quarkrad on 2011-06-29
liz@lizubuntu:~$ sudo blkid
[sudo] password for liz: 
/dev/sda1: UUID="edad6a75-8cff-495b-95f9-d67037bb660a" TYPE="ext4" 
/dev/sda2: LABEL="WINXP" UUID="EE80115F80113017" TYPE="ntfs" 
/dev/sda5: LABEL="HomeFiles" UUID="ae207b6d-9c06-4865-b0a4-4f3f16f60e25" TYPE="ext4" 
/dev/sda6: LABEL="HFCopy" UUID="7726AB6749D7F693" TYPE="ntfs" 
/dev/sda7: UUID="e928983b-2bc5-4b95-b692-a3999f2c217e" TYPE="swap" 
/dev/sdb5: LABEL="Images" UUID="10144AE6144ACE82" TYPE="ntfs" 
/dev/sdb6: LABEL="Backup" UUID="E65C87295C86F399" TYPE="ntfs" 
liz@lizubuntu:~$

---

### Post by seawolf167 on 2011-06-29
I had you repost the blkid info in case you had recently formatted the volume or something which would change the UUID.

Open /etc/fstab for editing
```
gksu gedit /etc/fstab
```
remove the line
```
UUID=ae207b6d-9c06-4865-b0a4-4f3f16f60e25 /media/sda5 ext4 user,gid=1000,uid=1000 0 0
```
add the line
```
UUID=ae207b6d-9c06-4865-b0a4-4f3f16f60e25 /media/homefiles ext4 defaults 0 0
```
at the bottom, save, exit, restart and see if it automounts correctly at /media/homefiles.

---

### Post by Quarkrad on 2011-06-29
That's done it - many thanks for all your help, appreciated.

---

### Post by seawolf167 on 2011-06-29
Glad it is working now! :)

---

