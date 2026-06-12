---
title: "Partitioning Help."
date: 2010-06-12
forum: General Help
---

### Post by th0r_ on 2010-06-12
Have referred the following links for partitioning:
[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

[http://linuxplanet.com/linuxplanet/tutorials/3174/5/](http://linuxplanet.com/linuxplanet/tutorials/3174/5/)

I wanted to go ahead with advanced partitioning on a 40 GB hard drive before.

Kindly suggest me the ideal sizes for:

/
/boot
/home
/tmp
/var
/usr

From my understanding off the web I am going with the following:

/ - 500 MB
/boot - 100 MB
/home - 500 MB
swap - 1 GB (2x RAM)
/tmp - 1000 MB
/var - 1000 MB
/usr - 5000 MB
/data - 30000 MB (Personal Data)

Any suggestions would be appreciated.

---

### Post by prodigy_ on 2010-06-12
Are you sure you want to go through all this trouble? Having a separate partition for **/home** is reasonable, but beyond that...

If you have a SSD hard drive and are worried about its lifespan, just use tmpfs as described [here](http://ubuntuforums.org/showthread.php?t=1183113).

---

### Post by oldfred on 2010-06-12
There is no reason for the average desktop user to have all the system partitions separate. Servers, raid and a few other special cases may need some of the folders as partitions but they understand why and sizes.

Herman on advantages/disadvanges of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

I do have /home and a /Data partition, but the reason for the /Data is that I want to install multiple operating systems and use the data in all of them. The /home should not be shared with other operating systems, generally.

---

### Post by jerome1232 on 2010-06-12
Personally, if your going to go for any advanced multiple partition setup. I would use lvm, which allows you to easily resize your partitions while the system is running.

Start the partitions off rather small and increase their size as needed. With lvm you don't have to worry about the physical layout of your partitions.

There are few disadvantages, ie partitions can actually become fragmented themselves if you do a lot of resizing overtime (can be fixed).

---

### Post by th0r_ on 2010-06-13
Thanks for all the inputs. I'm going to do some more reading on this before I move with advanced partitioning. :D

---

