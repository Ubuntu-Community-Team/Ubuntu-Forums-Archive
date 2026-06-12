---
title: "BleachBit - Can't Wipe Free Space"
date: 2011-07-01
forum: General Help
---

### Post by jrd43 on 2011-07-01
I have a 500 GB hard drive connected via a SATA/USB adapter.  After connecting it, I did a basic format of the drive with no problem.  I then attempted the "Wipe Free Space" option under the File menu in BleachBit, selecting the external drive, and it began the process.  It gives me a time estimate of about 300 minutes, but, instead, after a few minutes it says "Done" and gives me the message "[Errno 27] File too large. Disk space recovered: 0 Files recovered: 0 Errors: 1"

What happened?  What do I need to do to get this volume wiped?  Thanks.

---

### Post by TeoBigusGeekus on 2011-07-01
Bleachbit's wipe free space is still experimental (afaik).
Try with dd
```
dd if=/dev/zero of=/dev/sda bs=1M
```
Replace sda with your actual device-hard drive; be careful with this, if you specify the wrong drive, all your data will be replaced by zeros.
After dd is done, you can format your drive to your preferred file system.

---

### Post by jrd43 on 2011-07-01
Thanks for the tip. I'd like to give that a try, but I can't seem to find out the names of any of the disks.  How/where are they named?  I've been an Ubuntu user for a year now, but I still have a hard time with basic stuff like this.  

I would just use Dariks' Boot and Nuke, but the screen/video card on the laptop I pulled the drive from is on the fritz.

---

### Post by jrd43 on 2011-07-01
Ok - disregard last post.  I figured out that the name of the drive is sbd1.  I ran the command the cursor dropped down to the next line.  Now I'm just waiting.  Thanks for the help.

---

### Post by Andrew.Z on 2011-07-02
jrd43 :  If the drive has a FAT32 file system, BleachBit 0.8.8 won't wipe more than ~2GB.  BleachBit 0.8.8 works better with modern file systems such as ext3, ext4, NTFS, etc.

A future version may fix this limitation.

---

### Post by jrd43 on 2011-07-02
Thanks for the info, Andrew.  On the advice of Teobigusgeekus and some other threads I ended up downloading the dcfldd package, ran....
[PHP]sudo dcfldd if=/dev/zero of=/dev/sdb1 statusinterval=10 bs=10M conv=notrunc[/PHP] ...went to bed and the next morning it said something to the effect of "No more free space."  I'm hoping that means it was wiped.

---

