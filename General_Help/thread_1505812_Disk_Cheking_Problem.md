---
title: "Disk Cheking Problem"
date: 2010-06-09
forum: General Help
---

### Post by BorisPlankton on 2010-06-09
Running 10.04LTS after recent upgrade (about 2 weeks). Suddenly having problem on booting. Disk checking keeps coming up and when I select automatic mend it just tells me that /tmp is not available. If I press I for ignore I seem to be fine and have not experienced any problems running Ubuntu. Can anyone offer any advice?
Thanks.
Paul

---

### Post by TeoBigusGeekus on 2010-06-09
Which drive seems to have the problem?

---

### Post by ajgreeny on 2010-06-09
To double check you can run the live CD and from that run ```
sudo e2fsck /dev/sdx#
``` where sdx#is a standard sda1 sdb2 etc etc according to your system partitions.  You may need to do that command for both root and home, if the latter is on a separate partition.

You must not try to run the command on a mounted partition, so if you have mounted either in the live CD to check you have the correct one, make sure you unmount before running the command.

---

### Post by BorisPlankton on 2010-06-09
Not sure I understand the drive question but will look more closely at the checking messages next time I boot.
I am booting from internal hard drive. Ubuntu says it is checking then says found errors and refuses to mend, saying it cannot find tmp/, leaving me with no option but to ignore.
Dual boot system with one hard drive given over to Ubuntu and only ubuntu.

---

### Post by ajgreeny on 2010-06-09
If you run the command ```
sudo fdisk -l
``` from terminal in ubuntu it will output the partitions on your machine and you can tell from that the ubuntu device name.  It will look something like this:-
   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381   83  Linux
/dev/sda2            1306       19668   147500797+  83  Linux
/dev/sda4           19669       19929     2096452    5  Extended
/dev/sda5           19669       19929     2096451   82  Linux swap / Solaris

```
You can use those device names, running e2fsck on all except the swap and extended ones.

---

### Post by BorisPlankton on 2010-06-09
aj thanks. Went through reboot again as follows:
After checking disk I have 'Errors were found while checking the disk drive for /
I then select F to fix errors and get 'The disk drive for /tmp is not ready yet or not present'
Selecting 'M' for manual fix gives 'Filesystem check or mount failed'.

I then chose 'D' to depart and lo Ubuntu is booting cleanly again. Well has done 3 times now. 

sudo fdisk -l gives

/dev/sda1   *           1       60059   482423886   83  Linux
/dev/sda2           60060       60801     5960115    5  Extended
/dev/sda5           60060       60801     5960083+  82  Linux swap / Solaris

I guess I will rest up now unless anyone tells me I should not. Be interesting to see what happens the next time Ubuntu goes for a disk check I guess.

Thanks for all your help.

---

### Post by Glix on 2011-05-07
I have the same problem, upgraded ubuntu last night from maverick, but if I try to skip, it changes to:
The disk drive for /tmp is not ready yet or not present
and if I skip that I get:
mountall: Plymouth command failedj
mountall: Disconnected from Plymouth

So I'm confused as to how I'm supposed to get to a place where I can run terminal.

---

