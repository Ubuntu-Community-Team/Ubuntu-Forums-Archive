---
title: "Need to repair bad installation."
date: 2006-04-09
forum: General Help
---

### Post by frankm on 2006-04-09
Hello everybody,

I'm new to ubuntu and linux in general.  Recently, on the advice of a coworker I attempted to upgrade ubuntu breezy badger (5.10) to dapper drake beta (6.10)?  I somehow botched the installation and thought  I could make things right by running apt-get -f or something of that nature to force it to install.  The machine now says that it is ubuntu dapper drake, however the whole system is hosed.  ](*,) 

- x windows will not start up (nvidia driver not working)
- no network connectivity
- no idea what else is broken

Since I have no idea what else could be broken I was thinking of re-installing breezy badger.  The main problem that I have is that when I try to re-install breezy it keeps trying to wipe out all the data on the drive.  I have some files on there that I dont want to get rid of in some of the user directories but have no way of backing them up nor getting them off the drive. 

Anybody have any suggestions as to how to be able to re-install breezy without having to kill all the data in the user directories? :-k

---

### Post by aysiu on 2006-04-09
So no live CD?
No external hard drive? iPod? Blank CDs?

---

### Post by trent dillman on 2006-04-09
When reinstalling, don't use the default patitioning and instead do expert, and don't format your /home partition (if that's how your setup is, anyways)...

---

### Post by frankm on 2006-04-09
[QUOTE=aysiu]So no live CD?
No external hard drive? iPod? Blank CDs?[/QUOTE]


I guess I can get my hands on a live cd, the problem is I dont have anywhere else to move the data to. :(

---

### Post by frankm on 2006-04-09
[QUOTE=trent dillman]When reinstalling, don't use the default patitioning and instead do expert, and don't format your /home partition (if that's how your setup is, anyways)...[/QUOTE]

I tried to do what you suggested, however the only thing that appears in ubuntu's partitioning program is something like: 

hde5 / ext3 285 gb
hde5 / swap 2.8 gb

(unfortunatley i'm not at the location with the box right now otherwise i'd be able to tell you accurate details.)

i tried to set it up so that it wouldnt kill the partition with the data but it would then generate an error about no root partition being setup and not let me continue. :(

---

### Post by aysiu on 2006-04-09
[QUOTE=frankm]I guess I can get my hands on a live cd, the problem is I dont have anywhere else to move the data to. :([/QUOTE] Well, with a live CD, you can repartition and create a separate data partition. Put your important files on the data partition and then reinstall Ubuntu on to the other partition.

Does that make sense? Do you know the steps involved?

---

### Post by frankm on 2006-04-26
[QUOTE=aysiu]Well, with a live CD, you can repartition and create a separate data partition. Put your important files on the data partition and then reinstall Ubuntu on to the other partition.

Does that make sense? Do you know the steps involved?[/QUOTE]

Thanks for the suggestion, I tried to follow your steps but unfortunatley my ubuntu livecd keeps mounting the swap partition on the hard drive.......... this is preventing me from using gparted to resize the data partition in order to free up enough space to do a new install. 

any thoughts on how to get the livecd to not use the swap partition would be greatly appreciated :mrgreen:

---

### Post by Hairy_Palms on 2006-04-26
issue the command 
sudo swapoff -a
from the livecd to unmount the swap.

---

### Post by frankm on 2006-04-26
[QUOTE=Hairy_Palms]issue the command 
sudo swapoff -a
from the livecd to unmount the swap.[/QUOTE]

ok, i managed to get rid of the swap partition by deleting it,

the only problem now is that gparted doesnt seem to want to resize the ext3 partition 

it starts off running some sort of fsck command varient (eyfsck2k?) then the progress bar window disappears and it goes back to the point where as if I never asked it to resize the partition ](*,)

---

### Post by az on 2006-04-26
Bummer.  You probably could have fixed your video and internet with two commands.

sudo dpkg-reconfigure -phigh xserver-xorg

and probably sudo rm /etc/ndiswrapper/*

---

