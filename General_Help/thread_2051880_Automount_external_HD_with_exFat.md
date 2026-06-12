---
title: "Automount external HD with exFat?"
date: 2012-09-02
forum: General Help
---

### Post by Saturday76 on 2012-09-02
Hi,

I have problems getting my external hard disk with its exFat partition (for data exchange between Ubuntu, Win and OSX) automounted on my notebook running Ubuntu 12.04.1 LTS.

I have been following the instructions given here:
[http://linuxlife91.wordpress.com/2012/02/28/exfat-unter-ubuntu-11-10-nutzen/](http://linuxlife91.wordpress.com/2012/02/28/exfat-unter-ubuntu-11-10-nutzen/)

That's in German, and it basically says that automounting should work with the given instructions.

I have also added my user to the fuse group.

Manual mounting is working.

Some information about the involved hard- and software:
```
$ sudo lsusb
Bus 001 Device 004: ID 174c:55aa ASMedia Technology Inc. 

``````
$ cat /proc/partitions
   8       17  976759808 sdb1

``````
$ uname -r
3.2.0-29-generic

```It would be great if someone could give more some advice on this. If further information is needed, please tell me. Thanks in advance!

---

