---
title: "Problems with trying to remove partition-has keys by the name"
date: 2010-01-04
forum: General Help
---

### Post by babitweety06 on 2010-01-04
I am trying to reinstall ubuntu on my computer. I am now trying to create partition but I accidently created one that I do not want. Next to the name of the partition is a set of keys so I am guessing that it is locked. How do I remove that.

---

### Post by mcallenSchmee on 2010-01-04
Are you using GParted? Is the partition mounted? Try unmounting it first.

---

### Post by jamesisin on 2010-01-04
Yeah, you have to unmount a partition to modify it.  That's true whether using gparted or the new Disc Utility.

---

### Post by babitweety06 on 2010-01-04
it will not let me. It is saying that the cdrom is busy

---

### Post by babitweety06 on 2010-01-04
hi you replied to my post about creating the partition. I am really in need of help. I do not know exactly what happened to my computer. I just need help trying to install ubuntu again. So i have been trying to install ubuntu and i get to the partition page and its blank so i quit the installation and try to create a partition through gparted and i get stuck. I have this lock on this one partition. Its a key and i can not unmount because there is a message saying the server is busy.

---

### Post by jamesisin on 2010-01-04
> **babitweety06 said:**
> it will not let me. It is saying that the cdrom is busy

You can't change the partitions on a CD.

---

### Post by babitweety06 on 2010-01-04
its not a cd its a usb. theres still no way that i could delete it?

---

### Post by jamesisin on 2010-01-04
If it's a USB it should not tell you the CD is busy.

Unless you are running an ISO off the USB (which is a file pretending to be a CD).

A little more information on what you are doing will help us help you.

---

### Post by babitweety06 on 2010-01-04
that is true. I was reinstalling ubuntu. I downloaded it off of the ubuntu website. That file was a ISO so i used the pendelinx (i think thats how you spell it) program to load it onto a USB so windows can read it.

---

### Post by tmorphius on 2010-01-05
> **jamesisin said:**
> Yeah, you have to unmount a partition to modify it.  That's true whether using gparted or the new Disc Utility.
whats the 'new disc utility'??

---

### Post by jamesisin on 2010-01-05
Well, the USB partition surely isn't the partition you created by mistake.

Let's see the output of blkid (just put that into a terminal) and df -h (again, just put that in a terminal).

[noparse]```
copy this and paste your terminal results between these codes
```[/noparse]

---

### Post by babitweety06 on 2010-01-05
im not familiar with that term. the parition name is /dev/sda1

---

### Post by jamesisin on 2010-01-05
> **tmorphius said:**
> whats the 'new disc utility'??

My bad, correctly it's Disk Utility.  In 9.10 it replaces Partition Editor.  (Or more accurately palimpsest replaces gparted as the partitioning tool.)

---

### Post by babitweety06 on 2010-01-05
i dont understand what exactly you want me to tye in the terminal. Can you be more clear

---

### Post by jamesisin on 2010-01-05
```
blkid
df -h
```

---

### Post by babitweety06 on 2010-01-05
here are the results

Filesystem            Size  Used Avail Use% Mounted on
aufs                  896M   41M  804M   5% /
udev                  245M  240K  244M   1% /dev
/dev/sda1             1.9G  1.7G  216M  89% /cdrom
/dev/loop0            623M  623M     0 100% /rofs
none                  245M  100K  245M   1% /dev/shm
tmpfs                 245M   24K  245M   1% /tmp
none                  245M   84K  245M   1% /var/run
none                  245M     0  245M   0% /var/lock
none                  245M     0  245M   0% /lib/init/rw

---

### Post by jamesisin on 2010-01-05
That's df -h; how about blkid?

---

### Post by babitweety06 on 2010-01-05
nothing comes up

---

### Post by jamesisin on 2010-01-05
No output from blkid.  Odd.  Perhaps that's because you are running from the live CD.

I only see one partition on this system, namely the CD (USB) from which you are running the system.

Can you offer a screen shot of the utility showing the partition you are aiming to delete with the lock?

(Use the attach paperclip button in the Reply editor to attach your image.)

---

### Post by babitweety06 on 2010-01-05
here are the shots

---

### Post by babitweety06 on 2010-01-05
heres the shot where trying to unmount

---

### Post by jamesisin on 2010-01-05
That's your USB drive.  You are running your system off of that drive.  You don't want to unmount (let alone delete) that partition.

Try looking at that drop down in the upper right to see if there are any other partitions you don't like.  Post another screen shot if there are any other devices/drives we should look at.

---

### Post by babitweety06 on 2010-01-05
ok so i was trying to install this on the computer. how am i to install it. when i get to the partition faze there are no options for me to choose from. so what am i to do. It will not let me create one.

---

### Post by jamesisin on 2010-01-05
In the upper right corner there is a drop down where you will see /dev/sda (1.88 GiB).  Select a different drive.  If there are no other drives listed in that drop down, let us know and we'll think of something else.

---

### Post by Leppie on 2010-01-05
May I ask you what exactly you are trying to achieve?

> **babitweety06 said:**
> I just need help trying to install ubuntu again. So i have been trying to install ubuntu and i get to the partition page and its blank so i quit the installation and try to create a partition through gparted and i get stuck. I have this lock on this one partition. Its a key and i can not unmount because there is a message saying the server is busy.
Is this by any change an eee pc? You are installing from the usb pendrive to harddrive, sd, ?

> **babitweety06 said:**
> I was reinstalling ubuntu. I downloaded it off of the ubuntu website. That file was a ISO so i used the pendelinx (i think thats how you spell it) program to load it onto a USB so windows can read it.
Why do you need it to be readable by windows? Are you trying to do a wubi install (ubuntu within windows)?

---

### Post by babitweety06 on 2010-01-05
that was the only drive.
 
I am trying to install from ubuntu website to a windows computer from pendrivelinx to USB then to my laptop.
 
I am trying to reinstall ubuntu on my laptop. When I would turn on my computer the meter that tells the progress of the load up will freeze for two min and then a screen will come up basically saying that there was no operating system. So someone on here recommended that I reinstall the ubuntu software on the laptop. So from a windows computer I downloaded the software online. The file that they offer is ISO file. So inorder to have this put into a USB you have to change the file so windows can read it. And thats what i did using pendrivelinx. Now i have the software on the USB and trying to get it properly installed on the laptop. When I get to the partition faze of the installment I have no options to choose from and I can not even create a new partition. So i quit installation and tried to create a partition from the gparted. So basically i just need help with the partition part of the installation. I have a basic dell mini 9, no upgrades.

---

### Post by Leppie on 2010-01-05
> **babitweety06 said:**
> that was the only drive.
 
I am trying to install from ubuntu website to a windows computer from pendrivelinx to USB then to my laptop.
 
I am trying to reinstall ubuntu on my laptop. When I would turn on my computer the meter that tells the progress of the load up will freeze for two min and then a screen will come up basically saying that there was no operating system. So someone on here recommended that I reinstall the ubuntu software on the laptop. So from a windows computer I downloaded the software online. The file that they offer is ISO file. So inorder to have this put into a USB you have to change the file so windows can read it. And thats what i did using pendrivelinx. Now i have the software on the USB and trying to get it properly installed on the laptop. When I get to the partition faze of the installment I have no options to choose from and I can not even create a new partition. So i quit installation and tried to create a partition from the gparted. So basically i just need help with the partition part of the installation. I have a basic dell mini 9, no upgrades.
i'm very sorry, but i'm not familiar with the Dell mini 9 netbook. Did your netbook come with a 8gb SSD?

---

### Post by babitweety06 on 2010-01-05
It came with 4gb

---

### Post by Leppie on 2010-01-05
could you post the output of the following command:
```
$sudo fdisk -l
```

---

