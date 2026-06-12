---
title: "Removing a ssd from a system with two drives"
date: 2012-05-04
forum: General Help
---

### Post by Dry Lips on 2012-05-04
Hiya!

I've got one HDD and one SSD on a spare computer. Now I'm removing the SSD because I need it for another computer. I thought I could just remove the SSD and do a sudo update-grub afterwards, but after unplugging the SSD, I just get the grub rescue screen...

Setup:

sdb1 (=ssd) Mint12 (I'm removing this)
sda1 (=hdd) Ubuntu 10.04 server + XP (this is what I want to keep)

Now, what do I do?

---

### Post by arpanaut on 2012-05-04
From a live CD or USB with the 10.4 iso install grub on to the mbr of  sda

or while in live session chroot into the 10.04 install and reinstall grub then updatr-grub

another option is put the ssd back in and then boot to 10.04 and from there install grub to the mbr of that drive, 
after that it should boot without the SSD attached.

---

### Post by Dry Lips on 2012-05-04
> **arpanaut said:**
> 
another option is put the ssd back in and then boot to 10.04 and from there install grub to the mbr of that drive, 
after that it should boot without the SSD attached.

This solution was actually the easiest one for a lazy geezer like me! ;) Thanks a lot!
Somehow I was under the impression that the mbr was located on the HDD, but of course the MBR must have been on the SSD. 

So the MBR of the first HDD was actually deleted when I added the second drive and installed a new OS?

---

