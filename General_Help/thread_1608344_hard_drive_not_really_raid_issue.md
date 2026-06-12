---
title: "hard drive not really raid issue"
date: 2010-10-28
forum: General Help
---

### Post by kyotol on 2010-10-28
Running ubuntu 9.10. I installed win 7 the other day so I could play fallout new vegas and then fixed grub as usual. I played for a few days, then booted back to Ubuntu for my normal, stable, free life. I noticed my second storage hard drive wasn't mounted. I couldn't find it in the Places drop down menu to mount. When I open the Disk Utility is says: 1395 GB RAID Component.

This hard drive has never been part of a raid. It is just a storage drive formatted as ext4. I have about 1.1TB of movies, music, and whatnot on it. I don't want to loose all of those files. 

The result of sudo fdisk -l is:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee79ee79

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        2805    22427648    7  HPFS/NTFS
/dev/sda3            2806       91201   710040870    5  Extended
/dev/sda5            2806        3413     4883728+  82  Linux swap / Solaris
/dev/sda6            3414       64201   488279578+  83  Linux
/dev/sda7           64202       67982    30370851   83  Linux
/dev/sda8           67983       91201   186506586    b  W95 FAT32

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00071e95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      169633  1362577041   83  Linux
/dev/sdb2          169634      182401   102558960    b  W95 FAT32


How do I tell ubuntu that sdb isn't part of a raid and get my drive back like normal?

Thanks!

---

### Post by kyotol on 2010-10-30
I still cannot figure this issue out. Help?

---

### Post by ronparent on 2010-10-30
Depends on what kind of raid it thinks it is. If a 'fakeRAID' there will be symbolic links in the /dev/mapper location. For this case, a MB raid chip has been turned on long enough to write meta data to the drive. You usually can eliminate the problem by uninstalling dmraid. My preferred solution is to erase it and then dmraid has nothing to work with. To erase, in a terminal write 'sudo dmraid -E -r /dev/sda'. That should do it. Good luck.

---

### Post by kyotol on 2010-10-30
The only thing in /dev/mapper is a file called control. I cannot open it. 

I'm not sure how to tell if it thinks it is a fakeraid or not. Either way, it never was a raid disk and I def did not turn on anything in the motherboard bios. Disk Utility just labeled the drive, RAID component. 

I tried removing dmraid like you said, but all I get back is: "no raid disks and with names:" then whatever name I put. I tried every hard drive just to see what would happen. Same, nothing.

I appreciate the help though. Any other ideas?

---

### Post by kyotol on 2010-10-31
I guess I've lost of all of my data on that drive. Thanks for the help ronparent. I appreciate it.

---

### Post by ronparent on 2010-11-03
Try uninstalling dmraid (sudo apt-get remove dmraid)

---

### Post by kyotol on 2010-11-04
no luck, already uninstalled. Same issue.

---

