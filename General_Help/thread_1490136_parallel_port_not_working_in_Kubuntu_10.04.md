---
title: "parallel port not working in Kubuntu 10.04"
date: 2010-05-21
forum: General Help
---

### Post by pajaritoman on 2010-05-21
I have an old HP parallel printer plugged into my Monarch computer with two hard disks. 

On disk sdb I have Kubuntu 8.04.  This OS shows that a parallel port with the printer is recognized:

arl@cledus-b:/proc/sys/dev/parport/parport0$ cat autoprobe

MODEL:HP LaserJet 4ML;
MANUFACTURER:Hewlett-Packard;
COMMAND SET:HP ENHANCED PCL5,PJL,POSTSCRIPT;

On disk sda I have Kubuntu 10.04.  This OS shows no parport0 node in
/proc/sys/dev/parport/ and thus no printer.

I am wondering if the failure to recognize the parallel port in 10.04 is a bug or if parallel ports are too old to be included in new operating systems.  Anyone know of a workaround?

---

