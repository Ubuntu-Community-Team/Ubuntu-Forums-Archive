---
title: "Removing Ubuntu 11.04 Gparted"
date: 2011-08-30
forum: General Help
---

### Post by Bobrm2 on 2011-08-30
I wish to remove 11.04 from and reassign it's space to the Ubuntu 10.10, but am unsure how too.

  Have very limited knowledge of GParted, Do have the latest ISO, and have used GP once a long time ago. Will I disrupt or destroy the Hard Drive by removing 11.04 from it. Reading about GParted now.

Thanks
Bob

---

### Post by seawolf167 on 2011-08-30
Take a look at [this thread ]("http://ubuntuforums.org/showthread.php?t=1835546")- you can simply reassign the hard drive partitions/sizes/formats during the installation process. Rest assured you will not hurt the hard drive in any way - you will, however, need to backup all your personal information/files/etc. that you want to keep and transfer to your new installation.

---

### Post by Bobrm2 on 2011-08-30
What I wish to do is place a minimal system, without any frills in the deleted partition space, but in the mean time I've a space hog, probable having to do the Ubuntu 1 or Couch DB. All of this is of interest, but I don't know where to start picking the ball of string apart.

 So, I think and correct me please, I will clear up some space to add to the 10.10 partition, try to determine and correct the space hog, and finally start working with creating a minimal partition using this: [www.andyduffell.com/techblog/?p=689](www.andyduffell.com/techblog/?p=689). 

  I'm a glutton for punishment, and always pick the hardest road. Advice is most appreciated.

Bob

---

### Post by Bobrm2 on 2011-08-30
Seawolf, 
  Don't trust the Ubuntu 1 sync, but will it's use suffice?

---

### Post by seawolf167 on 2011-08-30
Here is the Ubuntu guide for the [Ubuntu Minimal installation]("https://help.ubuntu.com/community/Installation/MinimalCD").

[Ubuntu One ]("https://one.ubuntu.com/")is their cloud storage, I'm not sure what you want to do with this?

What do you mean by space hog? On your existing 11.04 system? Are you going to remove this system or try and work on it later?

---

### Post by Bobrm2 on 2011-08-30
I wish to remove the Ubuntu 11.04 and lease the 10.10 in place, find the space consuming problem and correct that, finally I want a minimal system, but leaving 10.10 in place (comfortable with it.
 I have the 11.04 on the other computer and with they had left the Gnome desktop alone. I'll change to Gnome 3 one day, I digress. Will read the link from you last post.

---

### Post by seawolf167 on 2011-08-30
Ok, I think I understand what you are looking for - all the formatting can be done through the use of a Ubuntu LiveCD (the installation cd). Boot up off it, then run GParted (System -> Administration -> GParted). From there, you can delete your 11.04 partition (this will remove everything, so ensure you have any backups you require), and reinstall 10.10 in its place (using the minimal installation image previously linked to). 

As always before you do partition editing and installations/re-installations, I highly suggest making a backup image of your entire hard drive with [Clonezilla ]("http://www.clonezilla.org")in case something goes wrong and you need to restore to your original point.

---

### Post by Bobrm2 on 2011-08-30
sudo: fdsk: command not found
bob@Ubuntu:~$ fdisk -l
bob@Ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a472

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      487424   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2              61        1028     7766016   83  Linux
/dev/sda3            1034        1642     4882432   82  Linux swap / Solaris
/dev/sda4            1642       14594   104036353    5  Extended
/dev/sda5            1642        2247     4862889   83  Linux
/dev/sda6            2247        6426    33563648   83  Linux
/dev/sda7           14537       14594      456704   82  Linux swap / Solaris
/dev/sda8            6426       14537    65150976   83  Linux

Are the two notifications important or just for general info?
1. Partition table entries are not in disk order
2. Partition 1 does not end on cylinder boundary.

---

### Post by seawolf167 on 2011-08-30
> **Bobrm2 said:**
> 
1. Partition table entries are not in disk order
2. Partition 1 does not end on cylinder boundary.

1. This just means that sda1 may physically occur after sda2
2. This is ignorable now-a-days

---

### Post by notgary on 2011-08-30
If you want to replace one Ubuntu installation with another, an easy way to go about it is to boot up your installation media as normal (I'm assuming you have a fully functional USB key or CD with the Ubuntu ISO already burned to it) and go through it normally until you reach the point where you choose where on the disk you want the installation to go.

Pick the option that allows you to manually partition your drive (I think it's marked as 'Something Else' from the list of options). You'll be presented with a partition editor similar to the one in GParted. What you do here is important. 

Select the partition that contains your 11.04 installation and mark it to be used as your root (/) partition. Now you have two options here:

1) Check the box that marks the partition to be formatted. **Warning: this will erase all your files and documents. Do not do this if you do not have a backup. If this is the case, option 2) is your friend.**

2) Proceed without doing anything else, **leaving the partition unformatted**. In this situation, the installer will overwrite the operating system files while leaving the contents of your Home folder intact. In theory, all your files should be safe, but it's always better to keep a backup with doing this sort of thing.

---

### Post by Bobrm2 on 2011-08-30
Thanks for you help. Have an ISO of Clonezilla, and 10.10. But the mini.iso would allow me to select to install the version I wish. Now for some study. Appreciate your assistance.

---

### Post by Bobrm2 on 2011-08-30
Have 11.04 removed, and no problems. Increased disk space, and now ready to assign a partition to a minimal version of Ubuntu. Thank you both for your help and input.

Bob R

---

### Post by notgary on 2011-08-31
Glad to have been of assistance :)

---

