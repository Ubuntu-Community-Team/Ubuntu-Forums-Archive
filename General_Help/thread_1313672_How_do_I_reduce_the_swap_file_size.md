---
title: "How do I reduce the swap file size?"
date: 2009-11-03
forum: General Help
---

### Post by 2048Megabytes on 2009-11-03
[SIZE="3"]When I originally installed Ubuntu I had about 900 megabytes of my hard drive dedicated to my swap.  When I upgraded to Ubuntu 9.04 it increased my swap file to 2 gigabytes in size.  How do I reduce the swap file to 900 megabytes in size?  I have 2 gigabytes of RAM and I don't need a swap file this large in size.[/SIZE]

---

### Post by SpitfireSMS on 2009-11-03
You can do this with a partition editor.
Get gparted-live, and boot from it.
This will allow you to resize your swap partition to whatever size you want, its really easy to figure out

---

### Post by Praxicoide on 2009-11-03
You can pop in a Live CD, choose "try Ubuntu without installation" and when it is running, type in a terminal "gparted", this should bring up Gparted, which is a partition editor. 

Needless to say, you have to be very careful when editing partitions, and have your important data backed up.

It isn't complicated, but still ask yourself if you really need that extra gig of hard drive space.

---

