---
title: "how to erase a virtual cd in a usb stick"
date: 2009-11-27
forum: General Help
---

### Post by kostaben on 2009-11-27
Hi forum

I have a usb stick of 2 Gb. When i plug it in apart from the usb stick a cd appears with some advertisment inside. I have not been able o erase it. I tried Gparted, Disk Utility and the dd command (dd if=/dev/zero of=/dev/sdg). All the above erase the contents in the Usb exept these 130 Mb of this "virtual" cd.
Is there a way to totally wipe the stik?

Best

k.

---

### Post by Arwen17evenstar on 2009-11-27
what does it do when you just right click on it and hit delete?
maybe that stuff is the usb required drivers?
other than that, try googling "clean usb stick" or something like that

---

### Post by sgosnell on 2009-11-27
Gparted should do it.  The files are in a separate partition, and you should be able to remove that partition, then resize the remaining partition, or you can remove all partitions and add a new one the full size of the drive.

---

### Post by paulgault on 2009-11-27
if you wanna do a proper job of it and go totally over the top you could try [killdisk]("http://www.killdisk.com/").
this will overwite EVERYTHING on the disk with zeros, including the partition table and everything. leaving you with a totally erased (and unrecoverable) drive. 
burn the .iso, have your flash drive plugged in and boot the CD. BE CAREFUL which disk you select as it will show the hard drives as well, as you don't want to do an unrecoverable overwrite on that (unless your selling an old hard drive on ebay)!!!
when your done you'll have to format the drive with gparted (or windows). and yes, as i said, this is a bit over the top.

---

### Post by kostaben on 2009-11-30
Thank you guys for the replies. The guys that put the adv there are good enough sgosnell, Gparted recognizes one 1,9 Gb partition and nothing more so its imposible to erase it. I think the only way is what paulgault said even though i would expect the dd command to do the trick.

---

