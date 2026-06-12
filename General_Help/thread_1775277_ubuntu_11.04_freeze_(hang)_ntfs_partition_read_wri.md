---
title: "ubuntu 11.04 freeze (hang) ntfs partition read write access"
date: 2011-06-04
forum: General Help
---

### Post by masuch on 2011-06-04
Hi,

I have installed Ubuntu 11.04 64 bit desktop version on ext4 partition without swap. I have maximus iv extreme motherboard with 8 Gbytes RAM. Using 3 internal ntfs formatted hard drives and 3 external ntfs usb 2.0 hard drives.
When I am trying to copy or move files FROM or TO any ntfs partiton it is 90 percent chance it is going to freeze. For copy/moving files I am using krusader run as ROOT or as user without root privilege or Nautilus as user without root privilege. It wasn't possible to switch to another terminal - it simply does not react on keyboard or mouse input and only hard reset is possible (scares me because of ntfs disks)

From this point of view I have suspicious on ntfs driver but: 
I am completely beginner in linux and I am looking for help to navigate me how to investigate to find what is causing the problem eventually to solve it? 

According to my experience it seems to does not matter if hard disk is internal or external connected through SATA II or SATA III or USB 2.0. I have tried to manipulate with ntfs partitions through the vmware or virualbox or truecrypt software or just do a simple copy/move files - it have has always the same results - freeze. There is not possible to say how long it is going to work properly and when it is going to freeze - sometimes it's working hour, sometimes it's working couple of seconds - no matter if it is read or write operation/s within ntfs partition.

Thank you for any clue and help.

---

### Post by russellwmy on 2011-07-04
I have same issue. It have happened since I did the packages update. below is the information of my computer.
cpu -> AMD Phenom™ X4 Quad-Core
display -> ATI Radeon 3200 HD
hd -> OCZ Vertex Series SATA II 2.5" SSD

---

### Post by masuch on 2011-07-11
Hi,

To continue to try to solve this problem: 
What I have changed from the last:
- compiled and installed new gcc and g++ 20110701 version.
- installed new kernel 2.6.39.2 (compiled by somebody else)
- patched and installed new catalyst 11.6
- installed new krusader 2.4.0 beta1
- installed new ntfs-3g 2011.4.12
- last ubuntu upgrades
- removed all ntfs mounts from /etc/fstab - now I am mounting NTFS or FAT32 only if I need it (I had automount on)

   All these stuff is quite fresh - about one week ago - so, there is no freezing :-) , but I will post, when something goes wrong. Within last week I used copy/move among ntfs disks rarely and I am not experiencing any freezing.
   Furthermore I am using virtualbox a lot. All *.vdi files are now located on ext4 partition/hd instead of on NTFS (I bought new HD because of it).

hardware:
 mobo:  maximus iv extreme (bios 1409)
 processor: intel i7-2600k (3.4Ghz - overclocked to 5.1 Ghz but still running on 3.4 - I do not know how to tell ubuntu to use 5.1 :-( but it is another learning))
 memory: 16Gb (overclocked to 1600)
 swap: no
 graphics: asus hd6990 (lower frequency)
 3 internal hard disks sata II or III - NTFS formatted.

I understand that what I did does not have to help to solve this problem - it could actually leads to more difficulties than before, but I have tried ;-)

-----
Is it possible to obtain the list what did you update/upgrade with version/s info? It could be useful for further investigation.
----

cheers

---

### Post by masuch on 2011-09-12
Hi,

Rarely it is going to freeze. Is there any way how to investigate what is wrong ? Is there some boot parameters to switch on to have more log details what happened ?

thanks,

---

