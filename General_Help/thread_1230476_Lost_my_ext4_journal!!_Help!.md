---
title: "Lost my ext4 journal!! Help!"
date: 2009-08-03
forum: General Help
---

### Post by jmcboots on 2009-08-03
I had a UPS fail, yesterday, thats another whole story, right now I am hoping I can recover a drive. When I reboot I got the fsck msg to manually fsck the drive. I did so and did a manual repair. However the drive will not mount. Here is my system. Is for the /home mount point. 

I have a two drive raid at /dev/md0.
I have LVM setup on top of that at /dev/homevg/homelv
Which is formated with ext4.

$ sudo lvscan
ACTIVE '/dev/homevg/homelv' [1.36 TB] inherit

$ sudo fsck.ext4 -p /dev/homevg/homelv
/dev/homevg/homelv: clean, 1336754/91578368 files, 183884442/366283776 blocks

$ sudo mount -t ext4 /dev/homevg/homelv /home
mount: wrong fs type, bad option, bad superblock on /dev/mapper/homevg/homelv,
missing codepage or helper program, or other error
In some cases useful info is found in syslog - try
dmesg | tail or so

When I check dmesg I get:
ext4: No journal on filesystem on dm-0

It appears that I have lost the journal somehow. Can that be right?

How can I fix this?

---

### Post by bodhi.zazen on 2009-08-03
I had a very similar problem with ext4 and was able to mount the partition after running fsck and then rebooting.

For mission critical servers I suggest you stay with ext3 :(

Here is my thread (HTH)

[http://ubuntuforums.org/showthread.php?t=1188782](http://ubuntuforums.org/showthread.php?t=1188782)

---

### Post by jmcboots on 2009-08-03
Thanks, I did see your thread earlier. But that did not help. It seams that after the initial single-user mode fsck, all subsequent fscks say the file system is OK.

That is until I go to mount it, when it says "No can do."

I think the data is still there since it reports back the number of files on the partition, but so far all attempts to remount it have failed.

I am hoping there is someway to mount the partition skipping the whole journaling thing. Then I can slurp the files off and rebuild the array using ext3.

Thanks for the tip though.

> **bodhi.zazen said:**
> I had a very similar problem with ext4 and was able to mount the partition after running fsck and then rebooting.

For mission critical servers I suggest you stay with ext3 :(

Here is my thread (HTH)

[http://ubuntuforums.org/showthread.php?t=1188782](http://ubuntuforums.org/showthread.php?t=1188782)

---

