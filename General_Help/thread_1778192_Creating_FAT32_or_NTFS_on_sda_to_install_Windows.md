---
title: "Creating FAT32 or NTFS on sda to install Windows"
date: 2011-06-08
forum: General Help
---

### Post by willsanderson on 2011-06-08
I never thought I would have to do this but I have to put Windows back on my linux
laptop. I will have to create a FAT32 partition and then the windows install disk will reformat as ntfs... right?
How do I do that? I have gparted installed. Any help.
Thanks,
Will

---

### Post by Habitual on 2011-06-08
after that install, you will have to re-install grub so have a LiveCD handy.

---

### Post by Mr. Shannon on 2011-06-08
I am assuming you want to erase Linux and that you have a windows installation disk (this should work for system recover disks as well).  If this is not the case then reply back with what you want to do with your Linux installation.

First you need to back up your files.

Then you need to load a Live CD and then in gparted right click on the swap partition and turn off swap.  Then use gparted to delete all partitions.  This will leave you with only unallocated space.  Windows installation disks will understand that, you don't have to format in fat32 first.

Finally, restart, remove the Live CD and insert the Windows installation disk and install Windows to the hard drive (you may have to explicitly create the NTFS files system during the installation, I can't remember).

---

### Post by oldfred on 2011-06-08
You do not have lots of room but can shrink the Linux partition and create a NTFS primary partition with the boot flag. Then the windows installer will find it. Make sure the partition is primary.

You have to use a LiveCD and use gparted from it. You may have to also click on swap and right click swap off. You have to use liveCD so all partitions are unmounted.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by willsanderson on 2011-06-09
Thanks oldfred, that sounds straight forward.
I do want to keep linux and just use windows for the occasional business ap I can't run or find in the opensource world.

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **willsanderson said:**
> I never thought I would have to do this but I have to put Windows back on my linux
laptop. I will have to create a FAT32 partition and then the windows install disk will reformat as ntfs... right?
How do I do that? I have gparted installed. Any help.
Thanks,
Will

Try installing VMWare in Ubuntu and you can install windows in Ubuntu if you need it. Worked for me. :) 

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

---

