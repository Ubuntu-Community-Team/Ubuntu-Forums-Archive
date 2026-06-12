---
title: "Making a Ghost image of hard drive"
date: 2010-10-06
forum: General Help
---

### Post by Ryan-Robinson on 2010-10-06
Hi guys,

Is there a software utility out there for Ubuntu that can make a backup of the hard drive my Ubuntu 10.4 is installed on?

I have used Symantec Norton Ghost for Windows before. Is there a similar program for Ubuntu?

I would also like to use the backup of the hard drive to reinstall on the same drive after a format.

Also, what would happen to the GRUB loader if I were to copy it back onto the hard drive?

Thanks,

---

### Post by nevius on 2010-10-06
[http://clonezilla.org/](http://clonezilla.org/)

I have imaged drives with multiple partitions / OSes without problems.

---

### Post by Ryan-Robinson on 2010-10-06
Thanks for your reply nevius.

What state would GRUB be in if I were to:

1. Image the drive
2. Format the drive
3. Install the image back onto the drive

I'm really firing in the dark on this one, but could I install the image back onto the drive and using the LiveCD reinstall GRUB?

---

### Post by trundlenut on 2010-10-06
why do you want to format the drive?  Clonezilla will just restore the disk as it was before but I don't think it touches the MBR.

---

### Post by skeetre on 2010-10-06
clonezilla should put your grub settings back, but yes, you could always use a live cd and do a grub-install that way.

I've used the simple dd to make a backup of a linux image, even cp -paRF / to another drive and back again worked after reinstalling grub.

The newer versions of ghost support linux drives if you have a copy of ghost. ghost4linux and clonezilla both work great though, and you can use the parted magic live cd to boot up and run ghost4linux.

---

### Post by Ryan-Robinson on 2010-10-06
Because I want to make sure that Clonezilla can do it properly and that I can do it right. 

And if my hard drive ever fails I can install the image onto a new one.

---

### Post by trundlenut on 2010-10-06
> **Ryan-Robinson said:**
> Because I want to make sure that Clonezilla can do it properly and that I can do it right. 

And if my hard drive ever fails I can install the image onto a new one.

fair enough.

Thinking about it, when I used clonezilla and I changed my hardrive over in my laptop it did copy grub and the MBR over ok.  But I presume it only does this if you choose the "entire disk" option rather than choosing an individual partition.

---

