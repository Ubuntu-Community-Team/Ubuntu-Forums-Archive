---
title: "frequent crashes on ubuntu 10.10"
date: 2011-04-25
forum: General Help
---

### Post by U235master on 2011-04-25
I recently switched from windows 7 to ubuntu 10.10 on my Gateway NV56 laptop. I previously had used wubi on it and had no problems, but with this installation it frequently crashes to a black screen and i have to reboot via the power switch. alt+sys-req+REUISB does not work, and i have lost a lot of data to this. my hardware is as follows
-AMD turiion X2 RM-75 2.5 GHz dual core processor
-ATI Radeon HD 3200
-4 GB memory
-500 GB SATA HDD
 -6 GB Ubuntu
 -41 GB linux swap
 -453 GB data

thanks in advance for any help you can give

---

### Post by KegHead on 2011-04-25
Hi!

Have you installed ATI drivers?

KegHead

---

### Post by U235master on 2011-04-25
i have installed ATI CCC version 2.13

---

### Post by KegHead on 2011-04-25
Hi!

Have you checked the software center?

also: system..admin...additional drivers?

KegHead

---

### Post by U235master on 2011-04-25
i dont know what i should look for in the software center. additional drivers showed that i was already using the AMD/ATI proprietary driver, and no other drivers were shown

---

### Post by KegHead on 2011-04-25
Hi!

I just noticed that your hdd is full?

Perhaps that's the problem?

KegHead

---

### Post by U235master on 2011-04-25
the 453 gb is mostly free space that i have dedicated in a partition for data, and is definitely not full

---

### Post by KegHead on 2011-04-25
Sorry!

software center..search..."ati"

KegHead

---

### Post by el_koraco on 2011-04-25
> **U235master said:**
> 
-500 GB SATA HDD
 -6 GB Ubuntu
 -41 GB linux swap
 -453 GB data

thanks in advance for any help you can give

Well, not to cause you further grief, but your partitioning scheme is not really good. 6 GB for the system will fill out very fast. 41 GB for swap is just... I've never even seen it. The swap partition is used in case the physical memory is too low, and does not need to be bigger than 6 GB in your case. You can keep a separate partition for data, but it is not necassary for it to be that large, especially if you no longer have Windows installed. 

You're probably thinking of it in the Windows kind of way. The "Ubuntu", or root partition is broadly analogous to the Windows C: drive. It is the partition that houses the installed programs and the files necessary for everything to work. The /home partition is broadly analogous to the Windows D. drive. It houses your user data. In case you need to reinstall the system, or even another Linux distribution, it can be left unformated. Most people have that kind of setup. Of course, you can keep an additional data partition if you want, but I would suggest a /home partition to be bigger, as well as the root partition. 

You can fix this on the go, but I would suggest that reinstalling might be easier. Before you do, read up on this tutorial, it is very extensive. 

[http://www.dedoimedo.com/computers/gparted.html]("http://www.dedoimedo.com/computers/gparted.html")

---

### Post by nothing.halo on 2011-04-25
I agree with el_koraco. I feel that you need to increase your partition size for Ubuntu, 6 gig is small. I have been running 10.10 for some time now and have not had any issues with it locking up or crashing.

---

### Post by U235master on 2011-04-25
i think what happened was while installing i mixed up the ubuntu and swap installations. i mean to put 40 gb for ubuntu and then 6 gb for swap, but somehow that got mixed up. would resizing the partitions from a usb help with the frequent crashes?

---

### Post by KegHead on 2011-04-25
Hi!

This might be helpful;

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

KegHead

---

### Post by el_koraco on 2011-04-25
You can always try resizing the partitions, but with your current scheme, I really do think you would be better off just reinstalling. It's not a long process. The crashes are, believe it or not, not your most pressing problem. This partitioning scheme is just not tenable. 

Of course, everything depends on how much data you have on the data partition and whether you have backups. 

Some suggestions for the new partitioning scheme: 

1.
30 GB for / (root)
6 GB Swap
The rest for /home
 
2. 
30 GB /
6 GB Swap
100 - 200 for /home
the rest for the data partition

Read up on partitioning in the tutorial I linked. You can use the Gparted tool that is on the Live CD or USB you made. Also, if you do have data on the data partition, I strongly suggest making a backup if you go into a scheme in which you will shrink the data partition, because there's just no way to guarantee you wan't lose any of it.

---

### Post by KegHead on 2011-04-25
Hi!

system..admin..language support.

KegHead

---

### Post by U235master on 2011-04-25
i am currently installing gparted on a usb and i will try to resize the swap first to 6 gb to free up around 34 gb of free space. i will then try to add that to the os install if i can. if that doesnt work, then i will just reinstall.

@keghead I already have the ATI proprietary fglrx driver installed and in use. that is probably the first thing i did once i got ubuntu booted up.

---

