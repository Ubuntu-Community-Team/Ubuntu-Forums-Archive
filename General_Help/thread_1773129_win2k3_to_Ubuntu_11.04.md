---
title: "win2k3 to Ubuntu 11.04"
date: 2011-06-01
forum: General Help
---

### Post by levidurfee on 2011-06-01
I am switching from Windows Server 2003 to Ubuntu 11.04.

These are two different machines, the Windows Server has 2 2TB Hard drives in it, that are setup as a RAID 1. The data on the drives is irreplaceable. I've scoured the internet for about two weeks, trying to find the best solution. It seems like everyone else had a slightly different setup, or the was no solution.

The Ubuntu Server has a 40GB SSD in it. I just installed a 2TB Hard drive (same make and model of the two in the Windows Server) and made the filesystem for it ext3.

First thing I did was just throw the 2 2TB Hard Drives in the new server, and tried to set them up as a software RAID. After it prompt me to erase the drives, I strayed away from that idea.

My end goal is having Ubuntu machine completely replace the Windows machine, so I'll need to setup Samba (which I'm sure I can figure that part out).

How can I get all the data off the 2TB Hard Drives that are using NTFS onto a RAID in the Ubuntu machine with an ext3 filesystem?

---

### Post by levidurfee on 2011-06-03
Should I create a software RAID with one of the 2TB Hard Drives like

```
mdadm --create /dev/md0 --level=1 --raid-devices=2 missing /dev/sda1 
```Copy all the data over the network to the new RAID, then put in one of the drives. Have it 'rebuild' the RAID array?

Something along these lines? [https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID](https://wiki.archlinux.org/index.php/Convert_a_single_drive_system_to_RAID)

---

### Post by nickpj on 2011-06-07
Hi Levidurfee,

Disclaimer: Entirely personal opinion, and I have only done this once! So I do not consider myself an expert, but I did want to document the steps I followed on the archwiki in case I ever needed to do them again.

Personally, I would buy a new 2 TB drive (cost would have to be less than US$100), and an external USB/eSata enclosure.

I'd then disconnect the cables from 1 of the 2 drives of the windows machine, and check it still boots windows okay, and can access at its data, with just the one drive. Presumably it should, if the RAID 1 is doing its job and working okay.

Then I'd take the disconnected drive, and put it into the new Linux machine, and the new 2 TB drive. During the installer, I'd choose the RAID option (I think it's one of the alternate disks - but this is not the steps I followed, so I don't know the exact steps needed - but if I was building from scratch now, then I would install RAID1 from the start, because manually converting from non-raid to raid is a hassle involving lots of steps, all of which you need to get right or it just won't work).

Then I'd set up the Linux machine as I liked it, configure everything, etc. Personally, the config I like is documented here: [http://nickj.org/Ubuntu_desktop_setup_steps](http://nickj.org/Ubuntu_desktop_setup_steps) 

Then I'd install VirtualBox, and set up the same or a later version of windows as I was used to in VirtualBox, so that you can still have access to windows (there's liable to be some program you need, or data that works best there, etc, so it's likely to be handy if you're migrating desktops). Steps are in the above web page, under the "VirtualBox" section.

Then I'd move the Windows disk into the external enclosure, connect it to the Linux machine, and copy the data off of it onto the Linux machine (either to your home directory, or into the windows VirtualBox).

Then I'd put the disk back into the windows box for a few weeks, until I was sure that all my data had come across okay.

Then I'd move the windows machine disk into the external enclosure, and either keep it as a snapshot of data, or format it, and use it as a target on the Linux desktop for "sbackup" (simple backup, which makes compressed backups of your data).

That's the approach I'd try. It seems the safest to me, with the least risk to your data. If you want to be extra cautious, you could buy 2 new 2TB disks, and that way you don't need to break the windows RAID array at the start. But I'd personally buy the extra disk and the external enclosure, rather than try anything fancy just to save the cost of one disk. Your time + avoiding the hassle of converting from non-raid to raid is worth more than the disk will cost.

Hope that helps!

-- All the best,
Nick.

---

### Post by levidurfee on 2011-06-17
So far I've managed to get two drives in the Ubuntu server and set them up as RAID 1. My next step is going to be copying all the data over. I'm assuming it will take about 20 hours to copy everything. I've got an external hard drive enclosure, I just hope it supports 2 TB. I just hope when I copy everything it adds Linux permissions, that's why I debated on copying over the network...:popcorn:

---

