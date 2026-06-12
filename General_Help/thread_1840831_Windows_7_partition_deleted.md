---
title: "Windows 7 partition deleted"
date: 2011-09-08
forum: General Help
---

### Post by Aaronneyer on 2011-09-08
When trying out Ubuntu on my computer, I accidentally deleted part of the Windows 7 partition.  
In Ubuntu installation, I chose to partition away 200 GB of my 600 GB  hard drive and format that as ext3.  After doing this, the other 400 GB  went from showing up as NTFS to "Unusable". 
Is this completely deleted or is it possible to recover it?  Not worried  about files as I backed up a few weeks ago so I don't have anything  important lost, I just want to get Windows 7 reinstalled without having  to buy a new license.
 
Additional Info:
Computer is Hp dv7-4285dx running Windows 7 Home Premium
HP has recovery software but it was unsuccessful when trying to do a restore.

---

### Post by evilsoup on 2011-09-08
I suspect you may be screwed (when dual-booting with Windows, you should *always* use the Windows tools to resize the partition, preferably after defragmenting the hard drive). However, you won't need to buy a new license, you should be able to get a Windows 7 disc from your manufacturer (HP).

---

### Post by Bodsda on 2011-09-08
> **evilsoup said:**
> I suspect you may be screwed (when dual-booting with Windows, you should *always* use the Windows tools to resize the partition, preferably after defragmenting the hard drive). However, you won't need to buy a new license, you should be able to get a Windows 7 disc from your manufacturer (HP).
 
You don't have enough information to make that assumption, you would need fdisk output or gparted.
 
There is no reason not to use gparted to do the partitioning, or the ubuntu installer for that matter. 
 
The Win7 disc/license will only be obtainable if proof of ownership can be provided. If the computer was purchased from a small retail outlet, rather than somewhere like PC-World, getting the license will be very difficult
 
Bodsda

---

### Post by Mark Phelps on 2011-09-08
Could be that the HP Restore doesn't work because you resized the original Win7 partition.  If you aren't worried about losing your files and apps, then read on ...

Boot with an Ubuntu desktop CD, open the Gnome Partition Editor and use the app to remove the Win7 OS partition and any Linux partitions.  This should leave the Recovery partition.

NOW, retry the HP Restore. With no partitions in the way, it just might work.

And NEXT time, BEFORE you start messing around with installing other OSs, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  You can use this to restore the Win7 boot loader and do other repairs.

---

### Post by evilsoup on 2011-09-08
@Bodsda: All I can say is that I once did the exact same thing as the OP (except with Vista), and no amount of scrambling around with gparted helped. If you know what you're doing, then yeah you can use the Ubuntu Installer to repartition; but the built-in Windows partition manager is generally safer when dealing with the Windows filesystem, for newbies. 

Anyway, my main point was that he doesn't necessarily need to buy a new license. Yes, he'll need proof of purchase (normally a receipt, though a credit card bill might be helpful, depending on local practice), but I would hope he would keep receipts around for something as expensive as a laptop.

---

### Post by Mark Phelps on 2011-09-08
<Removed -- duplicate post>

---

### Post by Aaronneyer on 2011-09-08
Tried deleting the drives and had no success there. Now instead of loading into recovery and failing to restore anything, recovery just doesn't show up.  I checked in Gparted and it shows the recovery partition but it says its not there when I try to boot into it.
HP has the recovery disks available for purchase online but does anyone know if there is a way to download them so I don't have to pay $15 to have HP ship them to me.

---

### Post by evilsoup on 2011-09-08
If HP or Microsoft don't offer them for download (I'm pretty sure they don't), then I'm afraid there is no legal way to get the recovery stuff without paying for it.

Assuming you have a Windows activation key (it should be printed on your laptop), if you have a friend with a proper Windows 7 disc you can use that - completely legally, iirc (you might want to check with Microsoft on that, though). Most people prefer Windows without all the junk laptop manufacturers pile on top.

If you are going to try this again, I recommend [this guide]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony").

---

### Post by nipunshakya on 2011-09-08
> **Aaronneyer said:**
> Tried deleting the drives and had no success there. Now instead of loading into recovery and failing to restore anything, recovery just doesn't show up.  I checked in Gparted and it shows the recovery partition but it says its not there when I try to boot into it.
HP has the recovery disks available for purchase online but does anyone know if there is a way to download them so I don't have to pay $15 to have HP ship them to me.

Okay, so if you are going with a dual boot, and you don't care whats inside your hdd, then i suggest you to start from fresh installations.....so you **first install windows 7 then go for ubuntu **(so as to avoid the issues with solving or repairing the GRUB if you install ubuntu first and then windows secondly). All you have to do is have a copy of windows 7 with yourself...(if you have the CD/DVD of the windows you installed previously, it'd be better).. then begin the installation of windows 7, format every single partition you have made so far and then choose wisely to install windows in some allocated primary memory.
Once installations are completed, run the Disk Management Utility to allocate partitions for your ubuntu...(suggested to go through windows disk management coz its user friendly)...then you can reboot to ensure your partitions are well set...and then go for installation of ubuntu via a LiveCD/USB whichever u prefer.....while installing ubuntu, you might as well want to make a good and wise partition for / , /home and swap too....choose wisely....

and yes, if you want some guidelines, check this out
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)  ):Pgoodluck.

Regards,WinuxUser

---

### Post by carolinason on 2011-09-08
it *might* be that you simply corrupted a partition table. boot into system rescue cd and run testdisk. save the table and see if it is bootable. if you resized the thing it should be usable.

i've definitely yorked a few installs back in the day and if you are like me and have really yorked the install, just install windows 7 and then install linux. as far as licenses go i can't help you there. i would hope the install disc came with your pc. if not just run linux! ;-)

welcome to linux. i hope you have fun.

---

### Post by Aaronneyer on 2011-09-08
Ok, just realized that my school offers me a free copy of Windows 7 Enterprise, so I'll just install that, then partition and reinstall Ubuntu.

Thanks for the help though guys.

EDIT:  Damn, actually it's just a free upgrade to Windows 7 Enterprise.
 
New question:
I purchased Windows 7 Home Premium a long time ago for my old computer, and I think I still have the ISO file somewhere.  Would I be able to use that and install it on my computer?

---

### Post by nipunshakya on 2011-09-08
> **Aaronneyer said:**
> 
New question:
I purchased Windows 7 Home Premium a long time ago for my old computer, and I think I still have the ISO file somewhere.  Would I be able to use that and install it on my computer?

If you got it inside your external simply burn that disk's image to a new DVD using ImgBurn(its good for windows 7) and then install it from the DVD.. Goodluck

---

