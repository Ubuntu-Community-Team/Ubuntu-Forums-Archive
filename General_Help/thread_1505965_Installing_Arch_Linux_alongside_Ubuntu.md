---
title: "Installing Arch Linux alongside Ubuntu"
date: 2010-06-09
forum: General Help
---

### Post by Axolotl9250 on 2010-06-09
Hi, this may not entirely relevant on a Ubuntu forum but I'm guessing  some users of multiple distro's may be able to help. I currently have  Vista, Debian and Ubuntu on my hard drive. I started out with Vista and  got introduced to Linux through Ubuntu and I want to try and dabble in  some other Linux Distros for the learning opportunity mostly. I have  already installed Debian and want to start having a look at that soon  but I would also like to have a look at Arch Linux. Now it has a good  Beginner's Guide for setting it all up but I'm a bit confused with the  partition of the hard drive part as in Ubuntu it does it all for you and  with Debian I simply cleared some space and chose the option to utilize  available disk space. The beginners guide shows how to do different  partitions and different types like root etc: 
Name    Flags     Part Type    FS Type           [Label]         Size (MB)
-------------------------------------------------------------------------
sda1               Primary     Linux                             15440 #root
sda2               Primary     Linux                             10256 #/var
sda3               Primary     Linux swap / Solaris              1024  #swap
sda4               Primary     Linux                             140480 #/home
and once those are created then you mount them. It says you can do this  in Gparted and skip straight to the mountparts bit. I assume if I make  some free space in Gparted in Ubuntu and make the partitions before I start and then skip to the  mounting and do this with what I create with the freespace the other  partitions will be left alone? Is it ok to put these new partitions I  would intend for Arch Linux together in an extended partition?

For the second part of my question: The beginners guide section about  the bootloader (GRUB) in the context of Arch Linux being the only  operating system on the computer, but with me this will not be the case.  Is there something different I need to do (My guess is there is but I'm  not sure what - messing around with the grub and stuff is very new to  me because so far Ubuntu and Debian has done it all itself). My install  order has been Vista, Debian, and then Ubuntu with live CD and guided  partitioning. So I think my GRUB is just that, not any other variant -  but whatever Ubuntu gave me (as its the one I installed last).

Thank you in advance to anyone who can help me with this. I shall be  asking the same question on the Arch Linux forum too after I register. 
Cheers :)

---

### Post by Citizen Bleys on 2010-06-09
My advice would be to skip the GRUB portion of the Arch install and continue to use Ubuntu's GRUB, since it's already working; just configure GRUB to point to the arch /boot (or /) partition to get it started.

I use the Ubuntu bootloader whenever I play with another distro just because I'm not going to be removing Ubuntu ever.

---

### Post by Axolotl9250 on 2010-06-09
Ok I shall try that, is this done through Ubuntu in a terminal or by accessing a file somewhere? I've not worked with or done anything to the grub before myself so I don't have much of a clue I'm afraid, sorry to be a nuisance.

This is my current partition system:
Model: ATA Hitachi HTS54252 (scsi)
Disk /dev/sda: 250GB
Sector  size (logical/physical): 512B/512B
Partition Table: msdos

Number   Start   End     Size    Type      File system     Flags
 1       32.3kB  42.5GB  42.5GB  primary   ntfs                                      <-Winows Vista.
 2      127GB   168GB   41.5GB  primary   ext3             boot                 <-Debian.
 3      168GB   250GB    81.7GB  extended                                          <- All  Ubuntu and the swap for debian is contained here.
 6      168GB    240GB   72.1GB  logical   ext4                                           <-Ubuntu
 7      240GB   244GB   3108MB  logical    linux-swap(v1)                         <-Debian swap
 5       244GB   250GB   6506MB  logical   linux-swap(v1)                          <-Ubuntu swap

The debian partition is labelled as boot and contains /boot/grub/menu.lst is this what I edit once I've installed Arch?

---

### Post by Penguin Guy on 2010-07-06
> **Axolotl9250 said:**
> The debian partition is labelled as boot and contains /boot/grub/menu.lst is this what I edit once I've installed Arch?
Yes, you'll just need to add an entry something like this:
```

# Arch Linux
title  Arch Linux
root   (hd0,**?**)
kernel /boot/vmlinuz26 root=/dev/sda**?** ro
initrd /boot/kernel26.img

```
**?** is the partition Arch is on.

---

### Post by snowpine on 2010-07-06
If the Arch Beginner's Guide is over your head, I recommend spending some time with Ubuntu and/or Debian first. Please understand I am not saying this to be condescending :) but rather because the Arch documention answers your questions in the clearest possible terms. Once you develop the necessary vocabulary (through using Ubuntu or Debian for a while), it will all make sense. 

One alternative you might consider is to create an Arch Virtual Machine. This will allow you to run Arch "inside" of Ubuntu, without actually partitioning your drive or creating a new partition. We have an entire sub-forum here that will talk you through the basics of virtual machines in Ubuntu: [http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by LowSky on 2010-07-06
Why do you have 2 swap partitions? You can use one swap for all your distros.

---

