---
title: "I Need To Install Ubuntu Server 10.14 On My"
date: 2010-10-24
forum: General Help
---

### Post by AnkurOn on 2010-10-24
I Need To Install Ubuntu Server 10.14 On My Pre-Installed Windows 7 64 bit.
I tried to install The ubuntu Server 10.04 , but when i enter my ubuntu CD in my laptop and try to boot from it It says that All the Hard Disk Will be erased and then Ubuntu will be installed.
I need to keep both the Operating system And make it dual boot . But It says that It will erase All the Data and i dont need to erase my data from my Hard disk .
I have Four drives of each 65 GB Each . But While installing it doesnt show up any of drives but shows directly Hard disk name . In that case i need a perfect guide so that i will be able to install the Ubuntu server With Windows 7.
Another question is that i have 4 partions but it shows none of them . shall i use Partion Magic Like software to make another partion of 30 - 40 GB ??? If yes please reply in thread .
Please Help me soon bcoz i need to install Server As soon as possible .
Ur's loving Ankur :)

---

### Post by Tyson S on 2010-10-24
First things first go to windows 7 inbuilt admin tools and check what drives are maped 

or

You say ubuntu sees it all as one disk just physically disconnect 3 of your drives during install let it erase the remaining connected drive and install then reconect all drives set boot priootiy to either os in bios and if you use 

windows 
download easybcd and install ubuntu bootloader to mbr

Ubunutu
run sudo apt-get grub and edit the menu.lst (i think this is not for grub 2)

---

### Post by AnkurOn on 2010-10-24
Hey Tyson . Actually i have Laptop And its in warranty  and your are saying to remove the next physical drives .
But i have one Hard Disk ! it's that i have 4 partioned drives On my Laptop  Not 4 different hard disk .
So what will be procedure And I know virtualization is possible but it takes up most of resources so i dont go for virtualization so i need Dual Boot !!! Need Help fast ......

---

### Post by Tyson S on 2010-10-26
go to ubuntu and type fdisk -l and see what comes up it may be not mounting the ntfs drives 

if not

in windows partition the ubunut partition as something wierd ie fat32 or HTFS or Ext3
and then write over the top using ubunutu server

---

### Post by SlugSlug on 2010-10-26
have you chosen to manually do partition druing install?

you should be able to just pick one partition and leave the others alone

---

