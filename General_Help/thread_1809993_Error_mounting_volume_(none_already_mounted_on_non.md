---
title: "Error mounting volume (none already mounted on none)"
date: 2011-07-22
forum: General Help
---

### Post by twipley on 2011-07-22
Hello. I have this internal (backups) hard disk drive of mine, which I cannot seem to get mounted. The error message I receive from "Disk Utility" is as follows:

```
Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, none is already mounted on none
mount failed

```

I have tried formatting, reformatting, always partitioning in the "ext4" file system, and rebooting, both using GParted and the bundled-in "Disk Utility," though to no avail -- the same error message always is springing up. Help; I am baffled, as a forum search returned nothing helpful.

EDIT: "sudo fdisk -l" reports, for reference purposes,
```
Disk **/dev/sda**: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007e72b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38913   312568641   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e48099e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         244     1951744   82  Linux swap / Solaris
Partition 1 does not end on cylinder boundary.
/dev/sdb2            4080       52219   386684550   83  Linux
/dev/sdb3   *         244        4079    30811136   83  Linux

Partition table entries are not in disk order

```

In short, cannot mount **/dev/sda** hard-disk-drive device. Any ideas?

---

### Post by twipley on 2011-07-22
It was working fine a few weeks ago, the last time it was plugged in. It is a working HDD, let us presume. The computer has not been moved since.

---

### Post by jamesisin on 2011-07-22
Slap it in a USB tray and see if the machine will mount that?

---

### Post by twipley on 2011-07-22
I am afraid I am lacking the necessary hardware to do so. Drive is working fine and is in good health; why would the system have problems all of a sudden in mounting it? It is just strange to me.

You know, usually (that is, when this hard disk drive is not internally plugged in) my primary drive is /dev/sda, but now it is /dev/sdb because the secondary (that is, the now-plugged-in drive) device itself is /dev/sda. I have just tried changing the SATA-plugs order on the motherboard, but the system did not boot up much past the BIOS that way, and I had to revert the changes. Am I looking at the right place?

(Sorry for having rejected that generous advice, by the way.)

---

### Post by twipley on 2011-07-22
For some reason "Disk Utility" was not able to mount or unmount the main partition of the device.

Since one partition of my primary hard drive is already mounted to /media/<filesystem_label>, the current partition of my secondary hard drive is going to be mounted to /mnt as its mount point.

First, to get an idea of the storage devices and related partitions, I am gonna fire up the "Disk Utility." Then, to make sure the wanted partition (in this case, /dev/sda1) is unmounted, I am gonna run

```
sudo umount /dev/sda1
```

until I receive the message that the partition already is unmounted (can take multiple times, depending on the number of times it already was mounted).

Then, I am gonna want to mount the volume if "Disk Utility" cannot:

```
sudo mount /dev/sda1 /mnt
```

where /dev/sda1 is the partition to be mounted, and /mnt is the mount point. Then, I want to naviguate to /mnt to access the partition.

In case nothing works, I am going to want to run the following commands:

ls -l /mnt -- to list current-directory contents

sudo chmod 700 -R /mnt/folder -- to re-appropriate read-and-write rights

sudo chown -R username:username /mnt -- idem; to change owner if necessary

sudo chown root:root /mnt/lost+found -- to chown back that folder to its default "root" owner

[SOLVED]

---

### Post by jamesisin on 2011-07-22
I'm not sure 700 is correct; I show read permissions for group on my /mnt folder.  Nice to see that was able to correct the problem though.  Permissions on /mnt/[mount folder] will cause problems.  Did you create this mount folder or was it system generated?

---

### Post by twipley on 2011-07-22
> **jamesisin said:**
> I'm not sure 700 is correct; I show read permissions for group on my /mnt folder.
Great idea. I myself am quite unused to using groups, so I overlooked the second digit and put it lower than it should have been by default.

> **jamesisin said:**
> Nice to see that was able to correct the problem though.
Thanks; indeed, that is nice to see. I am still wondering, though, what the causes of the issue were.

> **jamesisin said:**
> Permissions on /mnt/[mount_folder] will cause problems. Did you create this mount folder or was it system generated?
It was already there, so it is system generated. What kind of problems are you talking about, though?

Warm thanks for the conversation, by the way.

---

### Post by jamesisin on 2011-07-23
Weird errors when you try to do something mundane (such as you have experienced).  When I get an error I don't understand I first check permissions.

If you are going to create a manual mount for that drive, I would recommend doing so in /media.  I have an article about adding additional drives (though it needs rewriting):

[http://jamesisin.com/a_high-tech_blech/index.php/2009/01/ubuntu-gets-a-second-friend/](http://jamesisin.com/a_high-tech_blech/index.php/2009/01/ubuntu-gets-a-second-friend/)

---

### Post by twipley on 2011-12-27
I have never seen the issue again since Oneiric, so I guess if you are still affected by this and are using Natty, then it may be time for an upgrade.

---

