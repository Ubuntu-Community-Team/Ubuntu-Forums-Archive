---
title: "Create windows file system on USB stick with LIVECD"
date: 2012-05-24
forum: General Help
---

### Post by PhDJ on 2012-05-24
I am using Ubuntu on an USB-stick, I created a 4GB persistent linux file system on it, all works fine.

Now my question is if I can add a Windows file system to that stick so I can copy data to it and retrieve it on a windows system.

Do I need to use Gparted for that ?
Where can I find it under Ubuntu 12.04 LTS ?

---

### Post by roelforg on 2012-05-24
Gparted is the easiest.
 
Install/run on livecd (run in terminal):
```

sudo apt-get update
sudo apt-get install gparted
gksudo gparted

```

---

### Post by PhDJ on 2012-05-24
I finally found Gparted through the GUI.

Problem is although I now reinstalled Ubuntu on the key without making a persistent part of it, Gparted says there is no free space on the stick, so I can not add a FAT partition to it, I am not able to change the current one either to free up space.

---

### Post by roelforg on 2012-05-24
> **PhDJ said:**
> I finally found Gparted through the GUI.
 
Problem is although I now reinstalled Ubuntu on the key without making a persistent part of it, Gparted says there is no free space on the stick, so I can not add a FAT partition to it, I am not able to change the current one either to free up space.
 
Would it be an option to have gparted wipe the usb and redo the partitions the proper way?

---

### Post by PhDJ on 2012-05-24
> **roelforg said:**
> Would it be an option to have gparted wipe the usb and redo the partitions the proper way?

Maybe but that would mean losing my LIVECD installation !

---

### Post by PhDJ on 2012-05-24
When I try to access the persistent part of the stick I get the following message : Could not find "/cow". Please check the spelling and try again.

---

### Post by wilee-nilee on 2012-05-24
Windows will only read that partition for data if it is the first one on the stick.  So the second partition will be your ISO load with what ever sized persistent that can still be made.

If the stick is big enough you can have as big as you want a casper-rw partition rather then a file in the Linux that is usually limited to 4 gigs by most usb loaders. The casper-rw is the persistent part of the stick.

---

### Post by PhDJ on 2012-05-24
Whatever I try does not work.

I have a 8GB stick.

I have tried with a 4GB persistent part and a 2GB part.

I cannot access the persistent part in Ubuntu I get the following message : "Could not find "/cow". Please check the spelling and try again."

When I use Gparted in every case the stick is used for the full 8GB, I cannot add or change partition.

---

### Post by oklokl on 2012-05-24
# view
sudo parted -l

umount -l /dev/sdc1
umount -l /dev/sdc2
or

# ntfs
sudo umount -l /dev/sdc

# remove
dd if=/dev/zero of=/dev/sdc bs=446 count=1234

# make
sudo parted /dev/sdc
mktable
msdos
mkpart
0
-1
q

# format usb
sudo mkfs.vfat /dev/sdc1

or
sudo mkfs.vfat /dev/sdc2


# mount
udisks --mount /dev/sdc1



## parted 2 Partitioning
p # view
mkpart
0
50%
p

# end 4.0.0G    2 Partition
mkpart
start 4.0.0G
-1
p
q
sudo parted -l
# /dev/sdc1
# /dev/sdc2
sudo mkfs.vfat /dev/sdc1
sudo mkfs.vfat /dev/sdc2


#format ntfs
sudo mkfs.ntfs -f /dev/sdc1


#windows7 usb install
[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)
[https://launchpad.net/~colingille/+archive/freshlight]("https://launchpad.net/%7Ecolingille/+archive/freshlight")


deb [http://ppa.launchpad.net/colingille/freshlight/ubuntu](http://ppa.launchpad.net/colingille/freshlight/ubuntu) precise main  


sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CB7F5C71 ## winusb 



sudo add-apt-repository ppa:colingille/freshlight sudo apt-get update sudo apt-get install winusb Since WinUSB also works from the command line, you can create a  Windows 7 or Windows Vista USB installer by following the command line  format given below:
 sudo winusb --format <iso path> <device> Once the USB is formatted using the above method, install a Windows partition and edit the Master Boot Record:
 sudo winusb --install <iso path> <partition>

[http://moriskim.wordpress.com/](http://moriskim.wordpress.com/)
sudo winusbgui

---

### Post by Ubun2to on 2012-05-24
> **PhDJ said:**
> Whatever I try does not work.

I have a 8GB stick.

I have tried with a 4GB persistent part and a 2GB part.

I cannot access the persistent part in Ubuntu I get the following message : "Could not find "/cow". Please check the spelling and try again."

When I use Gparted in every case the stick is used for the full 8GB, I cannot add or change partition.

Windows 7 requires 16 GB of hard drive space to install x32 (20 GB for x64).
Windows Vista requires 40 GB of hard drive space w/15 GB free space.
Windows XP requires 1.5 GB of hard drive space.
I'm assuming you are using XP on this, as those requirements are for the lowest version (Home Edition on XP, Home Basic on Vista and 7, and Home Premium for Win 7 x64, as Home Basic only does x32; and has basically no features compared to other versions).
What I want to know is are you using this flash drive as an installer or an actual portable OS? If you're using it like a portable OS (where you just boot from the USB drive to access your data), I recommend a 64 GB flash drive (like [this one]("http://www.amazon.com/SanDisk-Cruzer-Flash-Drive-SDCZ36-064G-B35/dp/B005LFT37U/ref=sr_1_111?s=electronics&ie=UTF8&qid=1337853104&sr=1-111")), so you can have room for both OSs to do a full install, and still have leftover room for storing data. You can even get 128 and 256 GB drives, if you need lots of space (like you have no Internet usually, so having your media collection always with you is a must; if you work at a software dev company; or if you just like downloading big files for no real reason), or you just want bragging rights.
8 GB for 2 OSs (especially Lozedoze)? You've got to be crazy!

---

### Post by Mark Phelps on 2012-05-24
> **Ubun2to said:**
> ... 
What I want to know is are you using this flash drive as an installer or an actual portable OS? 

The OP clearly said in the first line of their post that they are using Ubuntu on a USB stick.

---

### Post by PhDJ on 2012-05-24
I think I gave everyone the wrong idea on what I want.

What I want is an USB stick with Ubuntu on it and on the same stick some room to copy data from my harddisk to that stick while I am using Ubuntu, after that I want to use the stick in Windows and read the data that I copied.

---

### Post by oklokl on 2012-05-24
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)
[ATTACH]218638[/ATTACH]

or Making room 

 Partition
 Division
All will recognize fat32 ..

Usb stick (Used repeatedly)
Data are contaminated well.
 Is not a good idea
Not booting usb os(Ubuntu installer)
 Occurs

---

### Post by wilee-nilee on 2012-05-24
> **PhDJ said:**
> I think I gave everyone the wrong idea on what I want.

What I want is an USB stick with Ubuntu on it and on the same stick some room to copy data from my harddisk to that stick while I am using Ubuntu, after that I want to use the stick in Windows and read the data that I copied.

Windows will only read the first partition on a stick. So the first partition on the stick has to be one it can read, a fat or ntfs basically.

---

