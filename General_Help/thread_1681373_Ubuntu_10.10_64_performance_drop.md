---
title: "Ubuntu 10.10 64 performance drop"
date: 2011-02-04
forum: General Help
---

### Post by tayga17 on 2011-02-04
Hi All

My freshly installed Ubuntu 10.10 64bit system after few hours of use becomes non-responsive. Its not completely frozen just very slooow. I can see it is accessing hard drive during that time. Please help me to find what is the cause of that.  

My mobo: Gigabyte p67a-ud5
Hard Drive: Caviar Black WD1002FAEX 1TB SATA3


Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             20184328   5382412  13776588  29% /
none                   4081756       256   4081500   1% /dev
none                   4088612      9876   4078736   1% /dev/shm
none                   4088612        88   4088524   1% /var/run
none                   4088612         0   4088612   0% /var/lock
none                  20184328   5382412  13776588  29% /var/lib/ureadahead/debugfs
/dev/sda3            925868672   6432236 872404988   1% /home
/dev/sdb             307666384  18240752 273797072   7% /home/tayga/Downloads
/dev/sdc             1922860936 796867652 1028317556  44% /media/URSA

---

### Post by mcduck on 2011-02-04
Any info about the rest of the system? How much memory you have? And what are you doing at the time with the computer?

Next time that happens, could you run "free -m" and post the output here. And also you'd probably want to check "top" or System Monitor to see if some program is using lot's of CPU time...

---

### Post by tayga17 on 2011-02-04
I have 8Gb DDR3 of RAM and i7 2600k CPU. It is always chromium and video player open when that occurs. And system becomes so slow that its almost imposable to open system monitor.

---

### Post by tayga17 on 2011-02-08
Thanks for advise 
I found out that it was flash plugin killing my system. I installed 64bit version and it stopped. 
However I did stress test and found out that its all fine until system needs to use swap. As soon as system runs out physical memory it becomes almost frozen. When I used "free -m" command from remote machine its outputted "segmentation fault". 

Does it mean i have problem with my hard drive?
Please help
Thanks

---

### Post by tayga17 on 2011-03-11
OK its solved
set AHCI mode for my drives in BIOS.

---

