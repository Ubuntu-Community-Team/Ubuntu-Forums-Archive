---
title: "DVD+RW Cannot fixate disk. K3B error message"
date: 2012-02-14
forum: General Help
---

### Post by sdowney717 on 2012-02-14
Any ideas on what this means?
Could it be that not enough space on the disk to finish writing?
1st time was this
> Fixating...
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 12.425s timeout 200s
/usr/bin/wodim: Cannot fixate disk.
Trouble flushing the cache
Fixating time:   12.425s
/usr/bin/wodim: fifo had 72674 puts and 72674 gets.
/usr/bin/wodim: fifo was 0 times empty and 39593 times full, min fill was 93%.

2nd time trying says this
> Fixating...
Errno: 5 (Input/output error), flush cache scsi sendcmd: no error
CDB:  35 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
Sense Key: 0x3 Medium Error, Segment 0
Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 57.754s timeout 200s
/usr/bin/wodim: Cannot fixate disk.
Trouble flushing the cache
Fixating time:   57.754s
/usr/bin/wodim: fifo had 72674 puts and 72674 gets.
/usr/bin/wodim: fifo was 0 times empty and 39887 times full, min fill was 84%.

cdrecord command:
-----------------------
/usr/bin/wodim -v gracetime=2 dev=/dev/sr0 speed=4 -sao driveropts=burnfree -data -tsize=2252892s -


---

### Post by jerrrys on 2012-02-15
check this out

[http://ubuntuforums.org/showthread.php?t=988813](http://ubuntuforums.org/showthread.php?t=988813)

found here

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Cannot+fixate+disk&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Cannot+fixate+disk&sa=Search&cof=FORID:9)

---

