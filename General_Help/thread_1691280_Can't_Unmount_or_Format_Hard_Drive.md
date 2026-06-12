---
title: "Can't Unmount or Format Hard Drive"
date: 2011-02-19
forum: General Help
---

### Post by jchase45 on 2011-02-19
I want to install windows on a free hard drive I have but the windows instalation said it can't install cuase it needs NFTS. So when I go to format and unmount my hard drive in Ubuntu I get this error 
[PHP]


Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda1 from /



[/PHP]

---

### Post by cogier on 2011-02-19
Windows will not see Ubuntu but Ubuntu will see Windows.

If possible install Windows first then Ubuntu.

You could remove the Ubuntu hard drive and install Windows then put the Ubuntu hard drive back. (You may need some extra help with Grub which I can't help you with)

---

### Post by jchase45 on 2011-02-20
I don't need it to see it I just want it to format and or unmount

---

### Post by cottfcfan on 2011-02-20
Try using the gparted live Cd instead.
You can get it from here:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by jchase45 on 2011-02-20
When I try gparted from Ubuntu I get these errors 


[PHP]

The partition could not be unmounted from the following mount points:

/

Most likely other partitions are also mounted on these mount points. You are advised to unmount them manually


[/PHP]

---

### Post by ephmanjmm on 2011-02-20
Boot from the LiveCD and use gparted.  You most likely will not be able to unmount / if you are using it for the running OS.

---

### Post by jchase45 on 2011-02-20
There is no RUNNING OS on it. I have 2 seperate drives , well 3 if you count my back up. 2 that have OS's instaleld. I have a lost Ubuntu install on the other one and now I can't acess it or format it or unmount it or anything.

---

### Post by jerenept on 2011-02-20
> **jchase45 said:**
> I want to install windows on a free hard drive I have but the windows installation said it can't install cause it needs NFTS. So when I go to format and unmount my hard drive in Ubuntu I get this error 
```



Error unmounting: umount exited with exit code 1: helper failed with:
umount: only root can unmount /dev/sda1 from /




```

You are trying to unmount the partition that holds the running OS. do not do this, choose another partition/hard disk to use. You can't unmount the partition mounted at "/". Ever.

Besides, you can delete Ubuntu partitions from the Windows install disc. They show up as "Unknown"

---

### Post by jchase45 on 2011-02-20
Let me repeat myself

> **jchase45 said:**
> There is no RUNNING OS on it. I have 2 seperate drives , well 3 if you count my back up. 2 that have OS's instaleld. I have a lost Ubuntu install on the other one and now I can't acess it or format it or unmount it or anything.

---

### Post by ephmanjmm on 2011-02-20
The error messages you posted state that you are trying to unmount / . 

Boot from the LiveCD, use gparted and partition and format the device you want to change.

---

### Post by mark bower on 2011-02-20
whenever i cannot get a HD to play friendly, whatever the problem or OS, i use an application called WipeDrive (probably a number of apps out there that do the same thing) to write zero's to the HD, ie, low level formating.  then the media on the HD is that of a new HD and I go from there.  so to format a HD with zeros, i "unplug" other HD's, set up the HD i want to "zero" as a master, boot with DOS off a floppy, then replace the floppy with my WipeDrive floppy and boot it.  slow, yes - but always get exactly what i want without aggravation.

i have been doing this for at least 7 years, and i always, always win.  i am not knowledgeable enuf to do it any other way althoh i did use Partition Magic in the past.

i dual boot with Ubu on one HD, XP on the other.  

mark bower

---

### Post by jchase45 on 2011-02-21
Ok well I managed to unmount and format MOST of my hard drive ( lol ) , but Ubuntu is taking 3 GB's hostage ( probably the 3 GB home folder I had encrypted and couldn't access)

I installed windows on the free partition I managed to save but now I can't make ubuntu boot , whats best way to rescue and make it bootable again?

---

### Post by mark bower on 2011-02-22
i probably should have mentioned, that after "zeroing" the drive, then i put XP on it.  then i put it back in the computer, reconnect to make the Xp drive the slave, then reboot.  if a problem with it booting first, then change boot order in BIOS.  then to boot to Ubu, then run "sudo GRUB-2" in terminal and computer boots showing choice of Ubu and XP.

actually, you can skip zeroing, and just run a new install of XP on the HD to be utilized.  this of course will allow for proper formatting and then the XP installation.  the key point of all this in the way i do it is to have the computer only able to access the one disk that XP is going to be installed on.  then put things back together where each HD is bootable, but set the Ubu HD to boot first.


mark bower

---

### Post by jchase45 on 2011-02-23
I've already installed my system I really don't want to have to re-install 

I jsut need access to a few files that I left on Ubuntu

---

### Post by jchase45 on 2011-02-27
bump

---

### Post by cottfcfan on 2011-02-27
Boot into your Ubuntu live cd and open a terminal:
Mount the partition containing the Ubuntu installation
eg.
```
sudo mount /dev/sda1 /mnt
``` if Ubuntu is sda1
then:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```
this will give Ubuntu control at Grub.
Reboot
When you boot into Ubuntu open a terminal:
```
sudo update-grub
```
Windows will now be added to your boot menu.

---

