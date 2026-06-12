---
title: "dd command not working"
date: 2010-05-28
forum: General Help
---

### Post by frank204 on 2010-05-28
iam trying to copy the nand image from my wm6 phone using the program"WM5torage"when i run this command:

dd if=/dev/sdb of=winmobile.img bs=512      i get the: dd: opening `/dev/sdb': Permission denied
ive tried sdb1 through sdb5 and get the same error.here is some more info:

Disk /dev/sda: 10.7 GB, 10737418240 bytes
255 heads, 63 sectors/track, 1305 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e733f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1244     9990144   83  Linux
/dev/sda2            1244        1306      492545    5  Extended
/dev/sda5            1244        1306      492544   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 129 MB, 129538048 bytes
1 heads, 19 sectors/track, 3329 cylinders
Units = cylinders of 19 * 2048 = 38912 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3329      126500    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sdb5               1        3329      126498    4  FAT16 <32M
Partition 5 does not start on physical sector boundary.
cadogan@cadogan-desktop:~$ 



Disk /dev/sdb: 129 MB, 129538048 bytes
1 heads, 19 sectors/track, 3329 cylinders
Units = cylinders of 19 * 2048 = 38912 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3329      126500    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sdb5               1        3329      126498    4  FAT16 <32M
Partition 5 does not start on physical sector boundary.
cadogan@cadogan-desktop:~$ 


here is the disk utility image also:

[http://i49.tinypic.com/hwx2tz.jpg](http://i49.tinypic.com/hwx2tz.jpg)

there are no options in wm5torage that says anything about allowing read write access.is there something i can do to change the permissions on that drive to allow it too make the image?thanks

---

### Post by lmarmisa on 2010-05-28
Maybe you have forgoten the sudo prefix:

> 
sudo dd if=/dev/sdb of=winmobile.img bs=512


---

### Post by frank204 on 2010-05-28
it worked but i cant find the file.where does it save it by default? this is the output:

119700+0 records in
119700+0 records out
122572800 bytes (123 MB) copied, 40.8628 s, 3.0 MB/s
cadogan@cadogan-desktop:~$ 


also what is the command too back it up "sector by sector"? thanks

---

### Post by lmarmisa on 2010-05-28
The file is saved in the working directory:

> 
[B]pwd
ls -l winmobile.img[/B]
Maybe you are looking for this command:

> 
**sudo dd if=/dev/sdb of=winmobile.img bs=512 conv=noerror,sync**


---

### Post by frank204 on 2010-05-28
thank you.:)

---

