---
title: "excessive ram usage by ubuntu"
date: 2009-08-28
forum: General Help
---

### Post by bulls_eye on 2009-08-28
Hi all,
I have installed Ubuntu 9.04 inside windows and pretty much everything is fine...
Only if I start linux dcpp the problems start appearing...
The system becomes very slow...

I used the free -mt command when linux dcpp was not running and this is the result i got...

owner@ubuntu:~$ free -mt
             total       used       free     shared    buffers     cached
Mem:           993        945         47          0        185        448
-/+ buffers/cache:        311        681
Swap:          255        115        140
Total:        1249       1061        188

I have heard that Ubuntu can run on machines with 256 MB ram, then why is it using so much ram in my case...

---

### Post by P4man on 2009-08-28
If I read that correctly, you are using just over 300 Mb. The rest is cache. Thats hardly excessive :) Run system monitor (system > administration) to have a more human readable output.

---

### Post by dmizer on 2009-08-28
Linux uses ram rather than disk swap for cache. That's why your ram usage looks high when it isn't actually high at all.

---

### Post by kpkeerthi on 2009-08-28
[http://www.linuxatemyram.com/]("http://www.linuxatemyram.com/")

---

### Post by bulls_eye on 2009-08-28
ok thats fine...
i got a bit confused by the format...
thanks for the help...
but then why does the system go slow on running linux dcpp??

---

### Post by P4man on 2009-08-28
are you using DC++ ?

if you run system monitor do you see excessive CPU usage? 
If you run "top" or "iotop" (<- to install run "sudo apt-get install iotop") do you see what processes are so busy ?

---

### Post by bulls_eye on 2009-08-28
yup,
i am usin linux dc++ ....

as per your advice I ran DC++ and then checked for cpu and memory usage...
i found out that dc++ used 15-20 % of cpu while genome-system-monitor used 20-30 % of cpu and these two were the major cpu consumers...

and even after runnin dc++ firefox vlc and update much of spare ram was left, so it is not due to the excessive usage of ram as i thought initially...

So u got any ideas to make dc++ usage smoother??

thanks a lot...

---

### Post by P4man on 2009-08-28
can you elaborate a bit more on the problem ? what becomes slow and when does it happen? When dc is launched ? or only when it is downloading fast ? is there excessive disk activiy ? Are you downloading to an NTFS volume? IF you think its an I/O thing, run "iotop "

---

### Post by bulls_eye on 2009-08-28
the system in general you know...
as soon as i launch dc++ for some time even the cursor refuses to obey my mouse...
vlc would give distorted sound for some time...

every new application will take grater time in its launch, even the terminal for that matter...

these problems are for some time after the launch; after that if i search something or download something then again they start appearing...

I use a variety of softwares like tor, vidalia, ipmsg, vlc, ktorrent etc.
but none of them is troubling me as much as dc++...

---

### Post by bulls_eye on 2009-08-28
I don't know the meaning of NTFS volume and I am also not sure that what you imply by i/o thing...

I have installed iotop as you adviced by I am not sure that what is it used for...

---

### Post by P4man on 2009-08-28
run iotop from a terminal It shows which processes are writing to disk (I/O)
NTFS is the file format for windows. Ubuntu can read and write it, but it does so badly (extremely slowly) on a drive with a small cluster size. You wont know what that means, but it doesnt matter.. what matter is... if you are writing to your windows drive from dc++ AND that windows drive used to be a FAT32 format that you manually converted to NTFS, THEN you could see very (extremely) poor performance. Thats a lot of IFs though...

---

### Post by bulls_eye on 2009-08-28
maybe thats the problem...
although i have never manually changed the format of my drives but as i mentioned i have installed ubuntu inside windows...

anyways man.....
thanks a lot for ur, help...

---

### Post by P4man on 2009-08-30
installing it "inside" windows doesn't mean you're writing to ntfs. A wubi install makes a (pseudo) Ext3 file system afaik, and that should be fine. A tad slower than a normal install perhaps, but nothing you would really notice.

If however, you are downloading (writing) to /media/disk or some place that is actually on the windows partition (or in other words, to a location you can read from within windows), then there is a small chance what I mentioned above is relevant.

But run iotop and find out whats going on.

---

### Post by bulls_eye on 2009-08-30
hi,

that's the case indeed..
my downloads go to media drive which is under the windows partition...
i ran iotop but i am unable to make any inferences...

i am copying the output here... 
please just have a look at it and tell me what's goin on

Total DISK READ: 237.59 K/s | Total DISK WRITE: 0 B/s
  PID USER      DISK READ  DISK WRITE   SWAPIN    IO>    COMMAND                                                                                             
 4065 root      118.79 K/s       0 B/s  0.00 %  0.00 % mount.ntfs-3g /dev/sda5 /media/Masti -o rw,nosuid,nodev,uhelper=hal,locale=en_US.UTF-8
 4100 owner     118.79 K/s       0 B/s  0.00 %  0.00 % vlc /media/Masti/Downloads/IN PANCHIYON(KMG).MPG
 4096 owner          0 B/s       0 B/s  0.00 %  0.00 % vlc /media/Masti/Downloads/IN PANCHIYON(KMG).MPG
    1 root           0 B/s       0 B/s  0.00 %  0.00 % init
    2 root           0 B/s       0 B/s  0.00 %  0.00 % [kthreadd]
    3 root           0 B/s       0 B/s  0.00 %  0.00 % [migration/0]
    4 root           0 B/s       0 B/s  0.00 %  0.00 % [ksoftirqd/0]
    5 root           0 B/s       0 B/s  0.00 %  0.00 % [watchdog/0]
    6 root           0 B/s       0 B/s  0.00 %  0.00 % [migration/1]
    7 root           0 B/s       0 B/s  0.00 %  0.00 % [ksoftirqd/1]
    8 root           0 B/s       0 B/s  0.00 %  0.00 % [watchdog/1]
    9 root           0 B/s       0 B/s  0.00 %  0.00 % [events/0]
   10 root           0 B/s       0 B/s  0.00 %  0.00 % [events/1]
   11 root           0 B/s       0 B/s  0.00 %  0.00 % [khelper]
   12 root           0 B/s       0 B/s  0.00 %  0.00 % [kstop/0]
   13 root           0 B/s       0 B/s  0.00 %  0.00 % [kstop/1]
   14 root           0 B/s       0 B/s  0.00 %  0.00 % [kintegrityd/0]
   15 root           0 B/s       0 B/s  0.00 %  0.00 % [kintegrityd/1]
   16 root           0 B/s       0 B/s  0.00 %  0.00 % [kblockd/0]
   17 root           0 B/s       0 B/s  0.00 %  0.00 % [kblockd/1]
   18 root           0 B/s       0 B/s  0.00 %  0.00 % [kacpid]
   19 root           0 B/s       0 B/s  0.00 %  0.00 % [kacpi_notify]
   20 root           0 B/s       0 B/s  0.00 %  0.00 % [cqueue]
   21 root           0 B/s       0 B/s  0.00 %  0.00 % [ata/0]
   22 root           0 B/s       0 B/s  0.00 %  0.00 % [ata/1]
   23 root           0 B/s       0 B/s  0.00 %  0.00 % [ata_aux]
   24 root           0 B/s       0 B/s  0.00 %  0.00 % [ksuspend_usbd]
   25 root           0 B/s       0 B/s  0.00 %  0.00 % [khubd]
   26 root           0 B/s       0 B/s  0.00 %  0.00 % [kseriod]
   27 root           0 B/s       0 B/s  0.00 %  0.00 % [kmmcd]
   28 root           0 B/s       0 B/s  0.00 %  0.00 % [btaddconn]
   29 root           0 B/s       0 B/s  0.00 %  0.00 % [btdelconn]
   30 root           0 B/s       0 B/s  0.00 %  0.00 % [pdflush]
   31 root           0 B/s       0 B/s  0.00 %  0.00 % [pdflush]
   32 root           0 B/s       0 B/s  0.00 %  0.00 % [kswapd0]
   33 root           0 B/s       0 B/s  0.00 %  0.00 % [aio/0]
   34 root           0 B/s       0 B/s  0.00 %  0.00 % [aio/1]
   35 root           0 B/s       0 B/s  0.00 %  0.00 % [ecryptfs-kthrea]
 4102 owner          0 B/s       0 B/s  0.00 %  0.00 % vlc /media/Masti/Downloads

---

### Post by P4man on 2009-08-30
Well, see if changing the download location to your homefolder or one of its subfolders changes the sluggishness  If it does, we can look further in to it, if it doesn't, then maybe its a dead track.

---

### Post by bulls_eye on 2009-08-30
actually the problem with that is there is very little space in my home folder to accommodate the files that i download from dc++...

anyways i will give it a try...

but still i dont understand that why it slows down the system when it is launched and when i am not downloading anything??!

---

### Post by bulls_eye on 2009-08-30
i tried that, but i didn't observe any noticeable change...

i would also mention that my sharing is also from the media\drive...

would changing that make a difference too??

---

