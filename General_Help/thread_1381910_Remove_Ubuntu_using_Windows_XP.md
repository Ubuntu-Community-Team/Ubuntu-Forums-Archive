---
title: "Remove Ubuntu using Windows XP"
date: 2010-01-15
forum: General Help
---

### Post by Johnny_Crunch on 2010-01-15
Hi All,
 
I have a dual boot system with Win XP and Ubuntu 9.10. 
My problem is, that I am not able to start Ubuntu anymore, it fails to boot. 
Actually I don't intend to repair it, instead I would like to remove it and free up the space used by the ubuntu partition on my hard drive. 
 
Is there a way to do that? 
 
It would be great to save some of my files kept in the linux filesystem, but I can live without them if that is not possible. 
 
Sorry if there was a thread already about this, I didn't find it. 
 
Many thanks

---

### Post by fancypiper on 2010-01-15
Doesn't Windows have a partitioning tool included (post win98 )? You could use that to change your partitions I would think.

Also you could boot with a Linux live CD and use it's partitioning tool to change your Linux partitions to NTFS.

There is a windows program available to read from Linux partitions.

[HOW TO: Mount Ext3 Filesystem in Windows](http://ubuntuextreme.blogspot.com/2009/01/how-to-mount-ext3-filesystem-in-windows.html)

---

### Post by lotharmat on 2010-01-15
Or go into windows disk management and just delete the partition that Ubuntu sits on and re-allocate the space to Windows.

---

### Post by lavinog on 2010-01-15
Keep in mind, if you delete your linux partition, you could be deleting grub, which would prevent you from booting to anything.
You will need to use the windows install disk to restore the mbr.

You could use the live cd to recover the files you need from the linux partition.
then remove everything except the /boot folder, then shrink the partition to only support grub.
You can then resize the ntfs partition to take up the free space.

---

### Post by Johnny_Crunch on 2010-01-15
Thanks for the help to everyone. 
 
Actually I haven't got the windows install disk. (it was preinstalled on my laptop, I have a recovery disk only, which would format the whole HD, and make a clean install..)
 
So I will have to try the second option what lavinog suggested.

---

### Post by lavinog on 2010-01-15
On my compaq, just booting to the recovery partition repairs the mbr.  If you go to the recovery partiton and reboot, and you don't get the grub menu, you might be ok.

---

