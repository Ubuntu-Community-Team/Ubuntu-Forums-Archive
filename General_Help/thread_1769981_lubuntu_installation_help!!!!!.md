---
title: "lubuntu installation help!!!!!"
date: 2011-05-28
forum: General Help
---

### Post by evilheart on 2011-05-28
hi , i am new linux user , i used ubuntu for couple of weeks now with different desktop environments , i installed it using wubi , because choosing a partition was quite confusing , and it crashed yesterday , so i was intending to make a fresh install of lubuntu .

and now :

first issue : the live cd didn't work , it gives me command line interface instead. also the CD name is install xubuntu , although it is sure the one of lubuntu!!! i install it from the official site of lubuntu.
i tried start x and it didn't work also.

i am still quite confused at the portioning step , i want to dual boot with windows , so i have to make partitions manually , what i understood from the guide was :

windows takes over all hard disk partitions , as all the hard disk is partitioned already into fat32 and ntfs drives , lubuntu needs space to make its own partitions , so i need to resize all my fat32 and ntfs partitions "or just some of them" so i can have empty space on the disk used for linux partitions "root , home , swap" .

now , i understood that repartitioning for lubuntu  will format my  whole hard disk , even if i resized my partitions , 
also i don't understand how automatic partition allocation of ubuntu is done , will it also format my whole hard disk?? 

what i decide is :
from  ubuntu installation , i will format one of my logical partitions into ext4 and make it my root partition , then i will skip creating home and  swap partitions , instead , i will make a swap file after the system is installed  , and home partition will be added to the root one by default , that way it won't be necessary to resize , repartition and lose all my data , and it will be somehow like installing windows "which is more familiar for me" .

my question simply is : WILL THAT REALLY WORK???? or there is a easier way to select one logical partition for lubuntu installation.

---

### Post by kerry_s on 2011-05-28
Sounds like a bad burn.
yes, 1 partition is fine, thats how I do mine.

i don't use windows no more, so i converted that to a network share. i'm using lubuntu 11.04.

---

### Post by linuxinstalledfromhdd on 2011-05-28
> **evilheart said:**
> hi , i am new linux user , i used ubuntu for couple of weeks now with different desktop environments , i installed it using wubi , because choosing a partition was quite confusing , and it crashed yesterday , so i was intending to make a fresh install of lubuntu .

and now :

first issue : the live cd didn't work , it gives me command line interface instead. also the CD name is install xubuntu , although it is sure the one of lubuntu!!! i install it from the official site of lubuntu.
i tried start x and it didn't work also.

i am still quite confused at the portioning step , i want to dual boot with windows , so i have to make partitions manually , what i understood from the guide was :

windows takes over all hard disk partitions , as all the hard disk is partitioned already into fat32 and ntfs drives , lubuntu needs space to make its own partitions , so i need to resize all my fat32 and ntfs partitions "or just some of them" so i can have empty space on the disk used for linux partitions "root , home , swap" .

now , i understood that repartitioning for lubuntu  will format my  whole hard disk , even if i resized my partitions , 
also i don't understand how automatic partition allocation of ubuntu is done , will it also format my whole hard disk?? 

what i decide is :
from  ubuntu installation , i will format one of my logical partitions into ext4 and make it my root partition , then i will skip creating home and  swap partitions , instead , i will make a swap file after the system is installed  , and home partition will be added to the root one by default , that way it won't be necessary to resize , repartition and lose all my data , and it will be somehow like installing windows "which is more familiar for me" .

my question simply is : WILL THAT REALLY WORK???? or there is a easier way to select one logical partition for lubuntu installation.

What you need to use to burn that ISO image is what I use on windows, and that is called infrarecorder.. Or IMGburn..   I don't know what application you used to burn it, but i would recommend you re-try with infrarecorder first.  See how that goes. 

Here is a nice walkthrough for Ubuntu 10.10

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

You can substitute Ubuntu for Lubuntu over here:

[http://lubuntu.net/blog/lubuntu-1010-released](http://lubuntu.net/blog/lubuntu-1010-released)

It's a bittorrent, so you will need to use that to download that ISO image.

---

### Post by wildmanne39 on 2011-05-28
> **evilheart said:**
> hi , i am new linux user , i used ubuntu for couple of weeks now with different desktop environments , i installed it using wubi , because choosing a partition was quite confusing , and it crashed yesterday , so i was intending to make a fresh install of lubuntu .

and now :

first issue : the live cd didn't work , it gives me command line interface instead. also the CD name is install xubuntu , although it is sure the one of lubuntu!!! i install it from the official site of lubuntu.
i tried start x and it didn't work also.

i am still quite confused at the portioning step , i want to dual boot with windows , so i have to make partitions manually , what i understood from the guide was :

windows takes over all hard disk partitions , as all the hard disk is partitioned already into fat32 and ntfs drives , lubuntu needs space to make its own partitions , so i need to resize all my fat32 and ntfs partitions "or just some of them" so i can have empty space on the disk used for linux partitions "root , home , swap" .

now , i understood that repartitioning for lubuntu  will format my  whole hard disk , even if i resized my partitions , 
also i don't understand how automatic partition allocation of ubuntu is done , will it also format my whole hard disk?? 

what i decide is :
from  ubuntu installation , i will format one of my logical partitions into ext4 and make it my root partition , then i will skip creating home and  swap partitions , instead , i will make a swap file after the system is installed  , and home partition will be added to the root one by default , that way it won't be necessary to resize , repartition and lose all my data , and it will be somehow like installing windows "which is more familiar for me" .

my question simply is : WILL THAT REALLY WORK???? or there is a easier way to select one logical partition for lubuntu installation.Hi, here is a link for dual booting with windows, please be careful when you do partition that you do not select to use whole disk. [http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

---

### Post by wildmanne39 on 2011-05-29
> **evilheart said:**
> hi , i am new linux user , i used ubuntu for couple of weeks now with different desktop environments , i installed it using wubi , because choosing a partition was quite confusing , and it crashed yesterday , so i was intending to make a fresh install of lubuntu .

and now :

first issue : the live cd didn't work , it gives me command line interface instead. also the CD name is install xubuntu , although it is sure the one of lubuntu!!! i install it from the official site of lubuntu.
i tried start x and it didn't work also.

i am still quite confused at the portioning step , i want to dual boot with windows , so i have to make partitions manually , what i understood from the guide was :

windows takes over all hard disk partitions , as all the hard disk is partitioned already into fat32 and ntfs drives , lubuntu needs space to make its own partitions , so i need to resize all my fat32 and ntfs partitions "or just some of them" so i can have empty space on the disk used for linux partitions "root , home , swap" .

now , i understood that repartitioning for lubuntu  will format my  whole hard disk , even if i resized my partitions , 
also i don't understand how automatic partition allocation of ubuntu is done , will it also format my whole hard disk?? 

what i decide is :
from  ubuntu installation , i will format one of my logical partitions into ext4 and make it my root partition , then i will skip creating home and  swap partitions , instead , i will make a swap file after the system is installed  , and home partition will be added to the root one by default , that way it won't be necessary to resize , repartition and lose all my data , and it will be somehow like installing windows "which is more familiar for me" .

my question simply is : WILL THAT REALLY WORK???? or there is a easier way to select one logical partition for lubuntu installation.
Hi, you do it this way you will have to reinstall grub because when you have to move a partition to make room for the swap it will not boot.

---

### Post by evilheart on 2011-05-29
> **kerry_s said:**
> Sounds like a bad burn.
yes, 1 partition is fine, thats how I do mine.

i don't use windows no more, so i converted that to a network share. i'm using lubuntu 11.04.

thanks guys ,
it seems that the iso is broken from the official site itself!!! , i burned ubunut 11.04 iso using the same application and CD drive and it worked "with some issue may be because of my low spec PC".
"== Lubuntu and official status ==

As said during the UDS session, we are on track for official status. Infrastructure issues are going to be solved and Lubuntu will be added to the list of flavors. We have all the authorizations for it, so I'm (Julien) pretty sure it will happen this cycle. We will have to work on stabilizing the new ISOs, but I'll write again when it will be available.
"


thats my disk info. using GParted from natty live cd , i have 2 HDDs one of 160 GB and the other is 80 GB , i want to install lubuntu on the partiton labeled amera , it is a primary one , of course without affecting any other partitions or data ,
 probably the windows boot loader is located there , but it doesn't matter as GRUB will do the job , right?

so , will my suggestion work? i mean in the installation i will format (amera) partition using ext4 format , make it the root partition for lubuntu , then skip making both the swap or home partions , instead i will make a swap file on the same partition latter as it have good space . 
will that affect my data or the other partitions???

sorry for the bad images!!!!

---

### Post by wildmanne39 on 2011-05-29
> **evilheart said:**
> thanks guys ,
it seems that the iso is broken from the official site itself!!! , i burned ubunut 11.04 iso using the same application and CD drive and it worked "with some issue may be because of my low spec PC".
"== Lubuntu and official status ==

As said during the UDS session, we are on track for official status. Infrastructure issues are going to be solved and Lubuntu will be added to the list of flavors. We have all the authorizations for it, so I'm (Julien) pretty sure it will happen this cycle. We will have to work on stabilizing the new ISOs, but I'll write again when it will be available.
"


thats my disk info. using GParted from natty live cd , i have 2 HDDs one of 160 GB and the other is 80 GB , i want to install lubuntu on the partiton labeled amera , it is a primary one , of course without affecting any other partitions or data ,
 probably the windows boot loader is located there , but it doesn't matter as GRUB will do the job , right?

so , will my suggestion work? i mean in the installation i will format (amera) partition using ext4 format , make it the root partition for lubuntu , then skip making both the swap or home partions , instead i will make a swap file on the same partition latter as it have good space . 
will that affect my data or the other partitions???

sorry for the bad images!!!!
Hi, you need to create the swap when you partition, one reason the swap is where the system stores the files when it goes to sleep, also if created after if you have to resize and move a partition to create the swap you will have to reinstall grub. You can get by without a home partition but it is much better to have one, especially on a separate partition that way if there is a problem you can reinstall and you do not loose any of your saved data,plus you can share like music and pics between say windows and lubuntu if you format it with ntfs.

---

### Post by evilheart on 2011-05-29
> **wildmanne39 said:**
> Hi, you need to create the swap when you partition, one reason the swap is where the system stores the files when it goes to sleep, also if created after if you have to resize and move a partition to create the swap you will have to reinstall grub. You can get by without a home partition but it is much better to have one, especially on a separate partition that way if there is a problem you can reinstall and you do not loose any of your saved data,plus you can share like music and pics between say windows and lubuntu if you format it with ntfs.

well i won't make a swap partition at all!!! i will just make a swap file and place it in the root partition as it have good space.
but i have another question : can i make one of my other logical drives as home drive , without formating it? it will be fat32 in that case , will that work? , also how will be the performance ? i know that linux work better with ext formats.

---

### Post by linuxinstalledfromhdd on 2011-05-29
You don't want a swap partition?  Can that actually be done?

---

### Post by evilheart on 2011-05-29
> **linuxinstalledfromhdd said:**
> You don't want a swap partition?  Can that actually be done?

in the past 2 weeks i was using ubuntu , which i installed using wubi , in wubi case there is no partitioning , you just choose a drive to install ubuntu like an application.but there is swap memory as usual.
so , yes i think it is possible , also while i was trying to install lubuntu i chose only a partition for root , when i tried to proceed  ,the installer just gave me warning that i didn't create a swap partition and asked me if i want to skip that.

well , that's somehow what my suggestion is based on , if it worked , then there is really no use of having a swap partition at the first place and putting the normal user in all this confusion!!!

---

### Post by linuxinstalledfromhdd on 2011-05-29
Wubi? Why don't you try installing it from a disc or live stick of USB?  You will have so much more freedom over your entire configuration that way.  Just a suggestion though.

---

### Post by evilheart on 2011-05-29
> **linuxinstalledfromhdd said:**
> Wubi? Why don't you try installing it from a disc or live stick of USB?  You will have so much more freedom over your entire configuration that way.  Just a suggestion though.

well , my wubi installation crashed couple of days ago , so i want to have a fresh live CD install of lubuntu  now , but the partitioning step is confusing , and i don't want to format my HDD by mistake or because of repartitioning , that's why i want to format just one main partition and leave all the other partitions and logical drives untouched.

---

### Post by wildmanne39 on 2011-05-29
> **evilheart said:**
> well i won't make a swap partition at all!!! i will just make a swap file and place it in the root partition as it have good space.
but i have another question : can i make one of my other logical drives as home drive , without formating it? it will be fat32 in that case , will that work? , also how will be the performance ? i know that linux work better with ext formats.Hi, here is a guide for gparted. 
[http://www.dedoimedo.com/computers/gparted.htm](http://www.dedoimedo.com/computers/gparted.htm) Yes you can use another drive or partition for your home folder, and it can be a windows partition so both systems can have access to those files,I am not sure how slow a fat32 will make ubuntu,I suspect not good, NTFS would be better. I am going to include a few links that you should look at because you will need to know the information. This one is how to partition.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
this one is how to install ubuntu on a second drive just in case.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html) This is for resizing.
 HOWTO: Mount NTFS partitions with specific ownership/permissions [http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

I know this is a lot to look at just take what you need a little from each guide and leave the rest for now.

---

### Post by linuxinstalledfromhdd on 2011-05-29
> **evilheart said:**
> well , my wubi installation crashed couple of days ago , so i want to have a fresh live CD install of lubuntu  now , but the partitioning step is confusing , and i don't want to format my HDD by mistake or because of repartitioning , that's why i want to format just one main partition and leave all the other partitions and logical drives untouched.

If you didn't backup your work, you will need to do data recovery with a live disc and an external drive to migrate your recovery data. Do you have that?  You will need to testdisk with a live cd of ubuntu, and locate the data you are missing at this point. 

You can install testdisk from terminal:

sudo apt-get install testdisk

And run it from root. 

Transfer anything it finds to your external. 

This is why it is important to always do backups before you make seriously huge changes to your computer. :)

---

