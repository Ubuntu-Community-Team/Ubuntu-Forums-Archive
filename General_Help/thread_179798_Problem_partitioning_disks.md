---
title: "Problem partitioning disks"
date: 2006-05-20
forum: General Help
---

### Post by thebrainchild on 2006-05-20
I am trying to partition my disk. It says the folliwng:

IDE1 Master (hda) - 12.1 GB FUJISTU MHK2120AT
          #1 Primary    4.8 GB (down facing arrow) FAT 32
          #5 logical      7.2 GB           fat32

I have not edited any of this yet (this was already there). What should I do next?

---

### Post by Ramses de Norre on 2006-05-20
Depends on what you're trying to achieve.. It looks like you've got two fat partitions now.

---

### Post by thebrainchild on 2006-05-20
I am trying to dual boot. What should I do?

---

### Post by Sef on 2006-05-20
> I am trying to dual boot. What should I do?

I would not recommend a dual boot with a 12 GB hard disk, not enough room for both.  

To read about dual booting, read this tutorial:

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

---

### Post by thebrainchild on 2006-05-20
That's actually the tutorial I was using. Thanks.

---

### Post by Herman on 2006-05-20
>  IDE1 Master (hda) - 12.1 GB FUJISTU MHK2120AT
          #1 Primary    4.8 GB (down facing arrow) FAT 32
          #5 logical      7.2 GB           fat32 I have installed Windows 98SE and Ubuntu Breezy Badger on a 6.0 GB disk, (splitting it 50/50) lots of times. That's how I experimented with the Ubuntu installer to find the info for the example installs on the website. I didn't care about adding too many files though, but there was still room for a few files.I have a new 30.0 GB disk in my test computer now though. 

If you have  two  blank DVDs  or a pile of blank CDs you might be able to copy all your data out of the 7.2 GB data partition to those. Your data should be backed up before beginning any partitioning operations anyway. 
A USB drive would be a lot easier if you can get one. There are lots of advantages for using a USB drive. Speed, ease of use, security (you can unplug it and lock it away whenever paranoia strikes) and portability to name a few.
After you have backed up all your data and you have double checked that it is all definitely copied safe and sound to whatever media you choose, you can proceed with your install.

You will need to go into 'Manual Partitioning' when you get to the [!!] Partition Disks Menu shown below.
[IMG]http://users.bigpond.net.au/hermanzone/p3/8ntfs.gif[/IMG]

You will need to select your old FAT32 data partition and delete the partition.

You will have 7.2 GB of free space. Just 'automatically partition' the 7.2GB free space and let the installer go! 
After the install you can put some of you data back if you want to. You will probably be able to fit nearly all of it back in if you put it in Ubuntu. You will still need Windows for a while until you convert your spreadsheets and wordprocessor files to Open Office.org. You can easily pass the files you need in Windows back and forth from Ubuntu because Ubuntu will have your Windows parition mounted. (With a white icon on your desktop).
 You'll find Ubuntu much better than Windows once you get used to it but that can take some time. Eventually you will want to delete Windows to have more disk space for Ubuntu. Then you will have lots of room.
All the best with it, Regards, Herman:D

---

