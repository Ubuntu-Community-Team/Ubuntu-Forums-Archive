---
title: "cloning my hard drive"
date: 2011-10-18
forum: General Help
---

### Post by carranty on 2011-10-18
Hi,

I have a 250GB hard drive and am running out of room.  I have a spare 500GB hard drive that I would like to clone my current HD onto, therefore giving me more space.  Yesterday I had both connected to my computer (sda and sdb respectively).  I ran the command 

[I]dd if=/dev/sda of=/dev/sdb 

[/I]which appeared to work, but when I remove the 250GB one and try booting from the 500GB one the computer won't boot, it just says 'invalid license'.

Any ideas what I did wrong?

---

### Post by carranty on 2011-10-18
I should just point out, after plugging my 250GB drive back in my computer works fine.

---

### Post by Grenage on 2011-10-18
I can see no reason for that not working, as long as the clone was completed.  I've not seen the "Invalid Licence" error before; at what stage was it displayed?  By that I mean, was it Grub/BIOS/Linux/windows?

---

### Post by aeiah on 2011-10-18
very strange error.. it sounds like something you may find on a locked down laptop, that only accepts an internal hdd with a particular serial number or something. but im guessing these are two external drives?

what does gparted say? are the boot flags and partitions the same? perhaps its an fstab error because /etc/fstab references the partitions on sda by uuid, and the uuids are different?

---

### Post by aeiah on 2011-10-18
also, you could try your luck with clonezilla, although dd should be the cleanest method

---

### Post by carranty on 2011-10-18
> **Grenage said:**
> I can see no reason for that not working, as long as the clone was completed.  I've not seen the "Invalid Licence" error before; at what stage was it displayed?  By that I mean, was it Grub/BIOS/Linux/windows?

It is right after the point the computer looks to see if there is a CD to boot from, and if not boots from the hard disk

---

### Post by carranty on 2011-10-18
> **aeiah said:**
> very strange error.. it sounds like something you may find on a locked down laptop, that only accepts an internal hdd with a particular serial number or something. but im guessing these are two external drives?


No, they're both internal, Desktop PC hard drives.  the 250GB is my primary hard drive (it has been the only one in my computer for the last few years), the 500GB is a used one I've aquired from a [no longer working] work PC.  Does it matter that I used the dd command to copy the 250GB drive while I was using it? i.e. should I use a live cd and use dd from that.  I left the computer to clone the drive overnight so wasn't actively doing anything but I guess background processes could change the contents of the 250GB drive whilst the copying process is taking place, thereby causing errors??

---

### Post by linuxwin2 on 2011-10-18
> **aeiah said:**
> also, you could try your luck with clonezilla, although dd should be the cleanest method
Try with clonezilla live CD
[http://clonezilla.org/]("http://clonezilla.org/")
[http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/]("http://geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/")

---

### Post by nm_geo on 2011-10-18
```
Does it matter that I used the dd command to copy the 250GB drive while I was using it? i.e. should I use a live cd and use dd from that
```
 
Yes.. Yes...  You can not have the drive mounted that are you are making a clone of. The CD or USB method will allow you to do it properly.  In fact I make a clone of my hard drive about every two weeks.  I do use Clonezilla it is faster than dd, but dd will do the job as well.  Depending on how much data it has to clone mine clones at about 1.6 GB through a regular USB connection.

---

