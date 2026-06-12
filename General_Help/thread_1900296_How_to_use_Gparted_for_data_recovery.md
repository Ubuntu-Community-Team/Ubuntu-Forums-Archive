---
title: "How to use Gparted for data recovery?"
date: 2011-12-26
forum: General Help
---

### Post by arnicainthemembrane on 2011-12-26
Hi. 

I tried to tweak my desktop settings through the command line and now my computer can't fully boot into ubuntu. I'm trying to figure out how to use gparted  to recover my files so I can back them up before doing a fresh install.

I don't recall what I typed or where I got the advice to do it. I had a fresh 11.10 install, didn't like the Unity desktop and   was attempting to revert to the Classic. Problem was, I used lines of code intended for 11.09 and now it won't fully boot up. 

Like an idiot i didn't back up all my data before doing this, so now I'm on data recovery mode. I know how to usb boot ubuntu and use gparted to play around with partitions, but i have no idea how to use it for data recovery, that is, how to access the files I still have on the computer so i can - finally - back them up and do a fresh install.

Any advice appreciated!

thanks!

---

### Post by fdrake on 2011-12-26
open the termina while in live session and type:
```

sudo fdisk -l    #(or just "fdisk -l")

```
copy and post here the output

you can use gparted to creat a new partition , data only. and resize the old one. move the file in the data-partition. delete all the other partitions and install the the new system next to the data partition

---

### Post by West201 on 2011-12-26
Use a liveCD and mount your Ubuntu partition. You can then install "testdisk", and run "photorec" in the terminal. Set the files to recovered to an external device.

It's pretty self explanatory once you run photorec.

---

### Post by The Cog on 2011-12-26
If you can boot from a USB stick, probably the best thing to do is to use the "try before you install" option. The file manager should allow you to mount the partitions on disk so that you can see the files you want to back up, and you should then be able to copy them to an external hard drive.

gparted is for editing the partition tables, and you certainly shouldn't try that until you have backed up your files.

---

### Post by arnicainthemembrane on 2011-12-26
thanks, i'll try that one. i figured there would be a way to access files already on a computer from a live usb "test run" install...

---

### Post by The Cog on 2011-12-27
Yes, I think you find all the drive partitions listed under Places. The only problem is figuring out which is which.

---

### Post by arnicainthemembrane on 2011-12-28
Okay, I managed to usb boot 10.04 as a test session. And I found the partition all right, and all my files/ folders were all there... except I now don't have the permissions necessary to open some of them! So I can't back anything up then freshly install. 

I attempted to install 10.04 (which I vastly prefer to 11.10)... first I followed the prompt to unmount dev/sda and dev/sdc, then was shown the partition table with 11.10 on it. However I can't boot into 11.10, that was the problem in the first place.  I want to take my home folder off of the 11.10 partition, throw it on an external hard drive, then install 10.04 and carry on... 

So...should I leave dev/sda & sdc mounted then install? 
Is there some way I can get permission to access the folders already on the "old" partition and back them up so I can do a fresh install?

Any advice?

---

### Post by The Cog on 2011-12-28
You should be able to gain access to all the files if you run your file manager as root. The command
> gksu nautilus will launch a file manager with full root privileges. If you prefer the command line, > sudo -i will raise your command prompt to root privileges where you can use cp, tar and other such commands with unrestricted access.

---

### Post by arnicainthemembrane on 2011-12-28
Tried gksudo nautilus, and file browser opened up with "root", giving me the ability to open folders which were formerly "locked". But now when I try to move them to an external drive, I am told "the folder (x) cannot be handled because you do not have permissions to read it".

---

### Post by arnicainthemembrane on 2011-12-28
whoops, tried sudo -i and it worked, thanks...

---

