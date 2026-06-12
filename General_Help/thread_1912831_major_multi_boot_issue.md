---
title: "major multi boot issue"
date: 2012-01-21
forum: General Help
---

### Post by fluft on 2012-01-21
hello 

a few days ago I had a healthy multi boot system, 

windows x2 , mac os , ubuntu , swap file and a storage partition.

I tried to backup and restore a windows partition, it worked but i lost grub2 and i had to use testdisk to recover the partition table, everything is o.k , but a few of the disk numbers have changed (sda numbers)

so i reinstalled grub2 via a livecd, restarted and yay grub2 sees everything!! and ubuntu is o.k. OSX works fine. Yet although windows is listed, when i click on windows the grub readout says something like this (so fast i had to take a blury photo to read it):

error no such device: (a load of numbers)
error device format "/dev/sda,msdos1" invalid: must be (f h dN, with 0 <=N < 120.

what i have noticed since my back up attempt is that a few drives are labelled differently, ubuntu is now sda7 instead of sda8 for example

So because i cant get into windows from grub2 menu, i fix the MBR of windows with this command

sudo lilo -M /dev/sda mbr

when i restart the PC grub2 is of course gone, but I can get into the two windows partitions.and they work great.

so i use a ubuntu live CD to reinstall grub2, But i am back to the problem where i can only get into ubuntu and OSX. where windows is listed in the grub menu, but i cant get access to it.


disk utility lists all partitions as healthy I can see xp osx ubuntu and swap.  However gparted says the whole drive is unallocated

so although all the OS's work great, I just can not navigate very easy, i have to use a live cd to fix grub switch between xp and ubuntu every single time i need to switch. 

I hope you can help, as i haven't a spare drive to back up and reinstall and i have a fair amount of valuable info on my ubuntu drive.


peace : )

---

### Post by 2F4U on 2012-01-21
For triple booting OSX, Windows and Linux it is usually recommended to install rEFit under OSX. Any particular reason for not using it?

---

