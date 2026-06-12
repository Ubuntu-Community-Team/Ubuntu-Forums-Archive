---
title: "dual boot windows 7 and ubuntu on two seperate HDDs"
date: 2011-07-08
forum: General Help
---

### Post by 987a654 on 2011-07-08
Got Windows 7 and ubuntu installed on two separate HDDs. 
They boot fine separately as Grub's the boot manager for Ubuntu HDD and Windows boot manager takes care of the Windows 7 Hdd.

I want to leave the Windows boot manager in the MBR of the Windows 7 HDD, that way I can save GRUB from bring overwritten whenever windows updates.

Now Grub manual says the following: 

>  If you have installed DOS (or Windows) on a non-first hard disk, you have to use the disk swapping technique, because that OS cannot boot from any disks but the first one. The workaround used in GRUB is the command drivemap (see drivemap), like this:

     drivemap -s (hd0) (hd1)

This performs a virtual swap between your first and second hard drive. 

I am planning on selecting the Ubuntu HDD as the primary boot device followed by Windows 7 HDD.

From what I understand I don't need to edit Grub 2, it should pick up on the fact that Windows 7 is not on the primary HDD and should implement the drivemap command automatically. 

Is this accurate?

---

### Post by 987a654 on 2011-07-08
> 
Ubuntu can only be installed after installing Windows 7


This is incorrect, I know it can be done. It really does not matter what order you install which OS.
Installing windows last writes it's own boot manager to the MBR thats why it's recommended to install Ubuntu last.

I am here to get some clarity as I am trying to set this up over a remote connection. The person helping me at the other end is not tech savvy.

---

