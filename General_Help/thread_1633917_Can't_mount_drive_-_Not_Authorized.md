---
title: "Can't mount drive - Not Authorized"
date: 2010-11-29
forum: General Help
---

### Post by skeam on 2010-11-29
Hi,

I'm building a media system based on Ubuntu 10.04.  I have an external 1 TB HDD that's connected to the system via eSATA.

Ubuntu sees the drive, but won't let me mount it.  Each time I click on it it says 'Not Authorized'.  The drive had been mounted on a system running NASLite-M2 (Linux-based) and it currently holds several hundred GBs of media files which I'd prefer not to lose.  I believe the drive is formatted to ext3.

I'm guessing that I need to find a way to use 'chown' and 'chmod' to get access to the drive, but I can't figure out how to address the drive or where I'd find it within the Ubuntu file system.

Any suggestions or ideas would be much appreciated!

---

### Post by blueridgedog on 2010-11-29
With the drive plugged in, what is the output of the command:

```
sudo fdisk -l 
```

Which of the fsisk's output do you think is the external drive versus known internal ones?

and 

```
mount
```

?

---

### Post by skeam on 2010-11-29
Hey blueridgedog,

Thanks for your reply.  Results of 'sudo fdisk -l':

```

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63558320

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121602   976762583+  ee  GPT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005335c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2490    19998720   83  Linux
/dev/sdb2            2490       30402   224197633    5  Extended
/dev/sdb5            2490        3237     5998592   82  Linux swap / Solaris
/dev/sdb6            3237       30402   218198016   83  Linux

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000af3fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30402   244197376   83  Linux

```/dev/sda is the 1TB drive I'm looking for and based on the warning message I see about GPT, I take it Ubuntu doesn't like that type of partition table.  Is there a way to keep the data and still get the drive mounted?

As for the results of 'mount':

```

/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sdb6 on /home type ext4 (rw)
/dev/sdc1 on /backup type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/soundwave/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=soundwave)

```Thanks very much!

---

### Post by srs5694 on 2010-11-30
The problem is *not* GPT; Linux works fine with GPT, although there are occasionally issues with buggy utilities or BIOSes.

The problem is most likely one of permissions. You should be able to overcome this problem with a few command-line commands:


[list=1]
[*]Type "sudo parted /dev/sda print" to view the partition table. (The fdisk output is useless for this purpose, since fdisk doesn't understand GPT.) This is just to figure out the partition number. It's *probably* /dev/sda1, but it's possible you must work with some other partition. Post the output here if you're in doubt.
[*]Type "sudo mount /dev/sda1 /mnt", changing the partition number if necessary. This will mount the partition at /mnt.
[*]Type "ls /mnt" (or "sudo ls /mnt" if the command without "sudo" gives you a permissions error) to verify that it's the right partition. You should see the files and/or directories you expect. If not, type "sudo umount /mnt" and post back with details for advice.
[*]Type "sudo chown -R yourname /mnt", changing "yourname" to your username, to change ownership of all the files so that you can access them. If you should have different ownership on different files, omit the "-R" to just change ownership on the root directory, which should at least enable it to be mounted. You'll then have to tweak ownership in a more specific way; post back what your situation is for advice.
[*]Type "sudo umount /mnt".
[/list]


At this point, the partition should be mountable via the GNOME file manager, and you should be able to access the files. If not, post back with more details, including any error messages you saw when following this procedure.

---

### Post by skeam on 2010-12-01
Hey srs5694,

Thank you very much for your reply.  Ran through the suggested commands (those are definitely some of the commands I'm still not that solid on).

Everything worked and I was able to mount the drive and transfer all of my data off of it.  I figure I can just format the drive now to ext4 and then figure out how to auto mount it somewhere else in the file system.

Thanks again!
Skeam

---

### Post by blueridgedog on 2010-12-02
I am curious to know the device that the drive came out of...GPT is not that common yet and I am surprised to see it in a hardware device.

---

