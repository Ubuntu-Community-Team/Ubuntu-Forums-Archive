---
title: "Dual boot Windows 7 and Xubuntu 11.10"
date: 2012-02-04
forum: General Help
---

### Post by arabuli on 2012-02-04
Hello, I have 300 GB harddrive and I want to dual boot Windows 7 and Xubuntu 11.10 from scratch.
 
I want 35 GB for Windows (and 100 mb for it's boot files)
10 GB for /
60 GB for /home
3 GB for swap
256 MB for /boot
 
And rest for DATA partition to store my movies, pictures, music etc.
 
Can you tell me how to achieve this? Whic OS should I install first? Which software should I use to partition my hard drive? Which partitions should be primary and which should be logical? Where should I install Grub?
 
Thanks.

---

### Post by LinuXofArabiA on 2012-02-04
I am no expert, but I will start the replies by weighting from the little I know. I would suggest you start with the Ubuntu installation, since Windows can be really fussy when it comes to sharing the HD with other OS's and given its NTFS format preference. 

That is my suggestion. Stick around for more, then you should get a clear idea.

---

### Post by holycow131415 on 2012-02-05
install windows first.

when its installed, go to disk manager to create a new partition/shrink the hdd. dont format it.

boot off xubuntu cd, start installing it, and you will be able to create  your partitions in the installer. partition the new partition that you  created in windows.

BTW, the partition for media that you want to share between windows and xubuntu needs to be formatted as ntfs.

---

### Post by WARS39 on 2013-04-25
I was informed that running a 3rd party partition program on a windows 7 OS is a very bad idea.

---

### Post by mkstallings1 on 2013-04-25
I would recommend installing Windows first, and then doing everything else with the Xubuntu install media.  It is made to do what you are wanting to do, whereas Windows seems to have been made to get in the way of what you are wanting to do.

---

### Post by mkstallings1 on 2013-04-25
Since you have the install media for both, it seems the worst that can happen is you have to start over again.

---

