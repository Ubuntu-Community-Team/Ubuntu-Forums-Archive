---
title: "Partition/Grub error lesson learned"
date: 2010-04-17
forum: General Help
---

### Post by la3875 on 2010-04-17
All, I have to share my frustrating experience today trying to repartition my drive to create a share between Ubuntu and XP. i am dual booting with XP the first install. I shrunk the Windows partition using EASUS Home Edition.  This resulted in a new partition between XP and Ubuntu. All appeared to go well until I rebooted. I got a no OS found and my heart started racing. Trying to stay calm I headed for the drawer for a copy of SuperGRUB. Armed with this I was able to restore the bootloader in the MBR and gained access to XP. 

I repeatedly tried to access the Ubuntu partition receiving errors 17 and then 15. After trying virtually all of the options on the SuperGRUB disk and several hours of time, my hope was waning. Doing a Google search for the grub error took me to a familiar place that has saved me more than once over the years I have played with Ubuntu - [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html) Persistence and patience paid off when I got to Herman's Legacy GRUB page. There was a an orientation and an example of the  /boot/grub/menu.lst file 

While browsing the menu.lst file I noticed my boot order was listed as (hd0,4). When I created the partition between the previous partitions, I effectively moved Ubuntu to (hd0,5). Changing all references to (hd0,5), and crossing my fingers on reboot, all was saved!

The bottom line here is the resources are out there and not panicking let me find them and save my installation. 

I hope this brief summary can help you too.
:guitar:

---

### Post by john newbuntu on 2010-04-17
Yep, that guy Herman has done a heck of a job in providing the community with Grub information.  I've learnt a lot from his notes and frequently refer his bookmarks to those who have problems.  Hats off to you Sir Herman.

---

