---
title: "SD Card mounts as read-only (Lucid)"
date: 2010-04-24
forum: General Help
---

### Post by cough on 2010-04-24
Hi,

Since I've upgraded to Lucid RC1, when I insert my SD Card it mounts as read-only. The write-protected switched isn't on and my card isn't corrupt.  I've tried chmod and chown to no avail. 

I'm wondering if this is a problem with Lucid....or Me? 

Does anyone know a work around so that I'm able to write to my SD Card?

Thanks in advance,

Kahlil

---

### Post by dcstar on 2010-04-25
> **cough said:**
> Hi,

Since I've upgraded to Lucid RC1, when I insert my SD Card it mounts as read-only. The write-protected switched isn't on and my card isn't corrupt.  I've tried chmod and chown to no avail. 

I'm wondering if this is a problem with Lucid....or Me? 

Does anyone know a work around so that I'm able to write to my SD Card?

Thanks in advance,

Kahlil

Do a fsck on it.

---

### Post by hkphooey on 2010-07-05
Strange. That happened to me as well. sudo fsck wouldn't run on it, sudo gparted wouldn't do anything to it. I ended up copying the files off the SD card, and doing 

sudo fdisk /dev/mmcblk0 

Then deleting the partition, and recreating it. (m to get the command menu) 

Then I could format it in gparted, and fsck it to my heart's content, and having formatted it, it now works fine. 

Not sure what the problem was. fsck was reporting a changed boot sector, but wouldn't let me alter it.

---

