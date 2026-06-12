---
title: "Re-partition Help"
date: 2011-03-16
forum: General Help
---

### Post by Patar on 2011-03-16
Hi, I have recently uninstalled ubuntu and I want to put the space I used for ubuntu back onto windows.I have 60.10 GB that I want to put into Disc C:. If anyone could help I would greatly appreciate it! :)

---

### Post by garvinrick4 on 2011-03-16
Windows has a partitioning manager to use. Since you do not have a Linux install anymore
you will have to use the Windows partitioning manager or download one like gparted in .iso and burn a disc. 
Google gparted or google Windows partitioning manager and will get results to read and learn. 
* There are Windows guys that dual boot and know how to use Windows if you want to
check back and see if you got a reply. Hope this helps you some.

---

### Post by Hedgehog1 on 2011-03-16
Here are the steps to getting your space back. 

First, get your PC to boot directly into Windows again:


To make a Windows 7/Vista emergency repair disk (in case you have not already made one):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

Boot from the windows 7 emergency repair disk, and do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-16
To remove Ubuntu and take the space back:

[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]


***The Hedge***

:KS

---

