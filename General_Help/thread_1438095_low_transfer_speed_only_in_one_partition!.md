---
title: "low transfer speed only in one partition!"
date: 2010-03-24
forum: General Help
---

### Post by kwstas on 2010-03-24
hi,

my system is a laptop(acer aspire 4810t) dual boot with windows vista.
i have ubuntu(karmic9.10) installed in sda3(/) and sda4(home) by ext3.

after a lot of testing, i have gathered these calculations each one after reboot:

> TO COPY A FILE OF 734453760 (700,4 mb)

from (home)sda4(ext3)
 to sda4: 4m53s
 to (/)sda3(ext3): 4m52s
 to (windows)sda2(ntfs): 4m53s
 to usb stick(fat32): 112 secs
 to usb external hdd(ntfs): 4m32 secs 


from (windows)sda2(ntfs)
 to sda2: 11 secs!
 to usb stick: 113 secs
 to usb external hdd(ntfs): 36 secs
does anyone has any idea of what could be wrong here?

---

### Post by Exca on 2010-03-24
Hi Kwstas,

Can you try to copy this file from your sda3 to sda3 ? Testing that can help to determine if you have a problem from the partition, or from the filesystem manager.

You can also try to check the consistency of this partition and try to repair eventual errors with : 
```
(sudo) fsck.ext3 -f /dev/sda4
``` -f to force the check, even if the disk seems to be clean.
Hope this can help,
Exca

---

### Post by kwstas on 2010-03-24
hi exca,

in order try sda3 to sda3 i had first to copy the file to sda3 so i did that i found out that the speed was the usual low one! apparently i had tested it before while the file was cached so it was copied fast. i have already changed that mistake on my post above also to sda2.
i'll try the code and let you know..

---

### Post by Exca on 2010-03-25
Here is a small test I've done with a 700 MB file:

Copy from a computer to another (both are ext3 partitions): 2min 30s.
Duplicate file on the same computer (on an ext3 partition) : 52 secs. (on an old IDE disk at 7200rpm)

What kind of disks are you using ?

Hope this can help,
Exca

---

### Post by kwstas on 2010-03-26
good morning,

on weekend i just tried to reinstall karmic (not the "home" partition though)
but i had no change!
i am now thinking of a way to backup "home" so as to reformat this partition also!
this of course is just a thought since i am not sure if it is right or wrong.


> You can also try to check the consistency of this partition and try to repair eventual errors with : 
 	Code:
 	(sudo) fsck.ext3 -f /dev/sda4 


do i have to do this by the live cd better maybe?



> What kind of disks are you using ?


it's a new laptop with IDE WD2500BEVT-22ZCT0
i found these details in BIOS.

---

### Post by kwstas on 2010-03-26
so i have used the live-cd and checked the sda4. -- no problems found!

i also managed to copy from sda3 to sda3(logged in as root) and copies normaly with no delays!
then (still logged in as root) tried to copy from sda4 to sda4 but the broblem remains!

so i guess the issue is on sda4 partition only, right?
in order to reformat only the sda4, should i just make these steps?

1) copy all data from "home" to another device
2) reformat sda4 only from live-cd in ext3
3) paste all "home" data in it

no need to use the "install-ubuntu" from live-cd for this?

---

### Post by kwstas on 2010-03-26
my problem is solved!

i was suggested to use a checkdisk utility from western digital for my hdd so i did or i tried to do. it gave me some error code before it even started to check! i just hope it was utilities issue...

so i just formated my "home" partition and copy speed is normal now!
i wasn't able to find anywhere instructions of how to do this so i made something wrong and had to reinstall both root"/" partition and "home" partition.

i had already made a copy of all of my folders in "user" folder of "home" so after the installation i just pasted them in my new "user" folder and that was it!

at the moment i have avoided formatting of my entire hdd which includes windows without having any issues...

---

### Post by kwstas on 2010-03-29
it seemed as my problem was solved but after i downloaded some new files i had the same problem!
i figured out that apparently "transmission" was responsible for this!
i also posted to their forums here [http://forum.transmissionbt.com/viewtopic.php?f=2&t=9811](http://forum.transmissionbt.com/viewtopic.php?f=2&t=9811)

---

