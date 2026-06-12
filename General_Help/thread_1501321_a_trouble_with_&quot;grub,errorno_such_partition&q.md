---
title: "a trouble with &quot;grub,error:no such partition&quot;"
date: 2010-06-04
forum: General Help
---

### Post by zonelight on 2010-06-04
I have a windows XP system and a ubuntu in my disk.Then i delete ubuntu with just kill the partition.After restart the system i saw the computer prompt me:
 
error:no such partition
grub rescue>
 
But that's not the all.I use WINPE and other ways for going back to my windows but the GRUB just told me the error.So i got my disk out and connected it to another computer then i format the C partition which has a windows xp.
But,it is very strange.When i took my disk back to my computer and just wanning to install a new XP system,the grub error just still............
 
So what i shall do now...............
 
One point is that i install the XP system by a usb key disk,as a reason about i do not have a CD or DVD ROM.

---

### Post by r_s on 2010-06-04
You will have to fix the mbr for the windows partition.
[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html)

---

### Post by zonelight on 2010-06-04
> **r_s said:**
> You will have to fix the mbr for the windows partition.
[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html)
I google it but many situations are the disk still has a XP partition in it,now in my disk there is no any system in it,i can not use the "fixmbr" command or any other mbr fix tools.
 
Oh,sorry. I know it,i need just take the disk to another computer= =.Thanks

---

### Post by oldfred on 2010-06-04
If you have your USB installer of Ubuntu, boot it and download and install this:

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr


Some of the rescue/repair CD that you can install to a USB flash drive have the lilo already available to use to  install to the MBR.

---

