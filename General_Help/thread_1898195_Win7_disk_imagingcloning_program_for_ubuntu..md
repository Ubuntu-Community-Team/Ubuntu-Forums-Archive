---
title: "Win7 disk imaging/cloning program for ubuntu."
date: 2011-12-20
forum: General Help
---

### Post by icgaln on 2011-12-20
I’ve become exceedingly frustrated in trying to do something I thought would be pretty easy to do. I just want to back up windows 7 install to an image then restore it. I really thought this would be easy but I have tried just about every program I can find and have had nothing but problems.
   
  The scenario I’m trying to create:
   
  Friend/relative rings up and says there computer has blue screen of death. I tell them to put the Ubuntu live cd I gave them into the there computer. Ubuntu loads up. I’ve got teamviewer working perfectly already so when Ubuntu loads teamviewer loads on startup and I can then remote view the computer from my computer at home. I then want to simply click on for example ‘Partclone’ load up a GUI and select the windows 7 system reserve partition and restore it from a backup image on there hard drive I put there when I first installed there computer. I then want to click the restore button and its now restored it. I then want to do the same for the main windows partition image I backed up. I then want to restart the computer tell them to take the disk out and then press enter. When there computer reloads it loads windows brand new like when I first gave it to them. Am I crazy to think I can do this easily?
   
  Ghost does it fine so does acronis and many other programs I have used that are installed on windows. But I have tried partimage, partclone, Qtparted, KDE Partition manager, clonezilla, mondo and a few others I cant remember the names of. All with varying degrees of success. Either I can install it but when I put the images back windows fails to boot in a number of ways. From giving a ctrl + alt + del message, inaccessible boot device to loading something windows related but then giving a blue screen or giving a recovery screen with the options to try booting normally or load recovery options. I can fix a couple of these problems by putting in a windows 7 disk and loading the repair option and it fixes the boot loader so it works but that isn’t helpful. Or I try and install the .deb package and find the program won’t install and needs dependency’s that conflict with other things I have or that I cant find and a mountain of other issues.
   
  Partimage I can install and make the images but when I restored them windows wouldn’t boot and it didn’t resize the partitions like ghost does which I would rather like it to. Same for KDE partition manager. Partclone I think I can get to install but I cant figure out how to actually load the program up and when I uninstall it in the software centre window once uninstalled it tells me ‘Sorry partclone is not available for this type of computer (i386) but it seemed to install the i386 package fine I could even get partclone.dd to spit out a load of text in the terminal but if I do just partclone nothing happens. The website shows a screen with a GUI so I assume it does have a GUI to run somewhere?
   
  I’ve similar problems with mondo and clonezilla. The .deb package for mondo needs dependency’s and I try and find some of them but they then want more dependency’s till I get to some I cant find at all. And everywhere I look on forums people keep recommending or saying ‘just use clonezilla’ but it’s a live cd and I tried following a guide to take a squashfs from the live cd and then doing something else with it but I couldn’t get the file to mount kept saying wrong squashfs type or something.
   
  I then tried installing VMware player and loading up ghost in it but it couldn’t see outside of the VM to backup the hard drive partitions. I also tried running just the ghost.exe in Wine but that had similar issues.
   
  Does anyone know of ideally a .deb package that I can just download and run and it will install a clone/disk imaging program that will work like ghost on ubuntu?
   
  I need it so when it restores it puts back on everything properly like the mbr and boot loader or whatever else seems to screw up. And also makes a partition the size of the restored partition automatically. Some of the ones I have gotten to work don’t do that I think.
   
  I’m starting to loose the will to live. I really thought this would be easy.
   
  Any help appriceated.

---

### Post by icgaln on 2011-12-21
Is it possible to image a Win7 install from an ubuntu live cd using the right program?

I've been trying to do it again with KDE Partition Manager and at least it installs and backs up an image. But when i put it back on a blank hard disk i just get windows boot errors or the partition type is put back as NTFS at first glance but when i check it’s actually saying it’s a Linux partition.

Anyone have a clue what I’m doing wrong or can point me in the right direction to something that just ‘works’ if i install it on Ubuntu?

---

