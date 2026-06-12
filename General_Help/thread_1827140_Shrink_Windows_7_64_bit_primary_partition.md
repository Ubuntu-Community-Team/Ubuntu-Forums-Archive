---
title: "Shrink Windows 7 64 bit primary partition"
date: 2011-08-17
forum: General Help
---

### Post by TE7 on 2011-08-17
Anyone know the best way to shrink the Windows 7 64 bit primary partition (C: drive)? The C: drive was originally just over 900 GB free space. I shrunk it using Windows 7 Disk Management, but it would only let me shrink to 468 GB, which I did. I want to shrink it to 100 GB. Will G-Parted work for this? Will I be able to boot into Windows after I use G-Parted? Or will I have to use the Repair Disc to fix Windows? If so, will the Repair Disc work. I have a new PC. I had Ubuntu 10.10 dual booted with Windows XP on my old PC. Any comments welcome.

---

### Post by oldfred on 2011-08-17
Windows works best if the NTFS partition has 30% free space. When you get down to 10% free it slows so much as to be about unusable.

Is this the Windows repairCD you made? You need to have a repairCD or liveCD/USB for every system installed & I like to have several Linux repair ISOs as alternatives.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by TE7 on 2011-08-17
I just want to know the best way to shrink the Windows 7 64 bit primary partition. Will G-Parted work? And will I have to use the Windows 7 repair disc to repair Windows (I have one already)?

---

### Post by fcomstoc on 2011-08-17
You don't really need a 3rd party partitioner, Windows come default with a partitioner in the control panel. If your Windows 7 works you can go into the control panel, type partition in the search box and the program shows up in the results. You can then shrink the windows partition, restart and install Ubuntu.

---

### Post by TE7 on 2011-08-17
Windows only lets me shrink to 468 GB. I want to shrink it to 100 GB.

---

### Post by fcomstoc on 2011-08-17
> **TE7 said:**
> Windows only lets me shrink to 468 GB. I want to shrink it to 100 GB.

Did you defrag your HD that usually frees up some space, Windows does a terrible job of managing HD space

---

### Post by TE7 on 2011-08-17
Yes I defragmented the hard drive. I think it's because of unmovable files.

---

### Post by fcomstoc on 2011-08-17
Another option that I have used on occasion is reinstalling windows, after a clean install you can usually shrink it as small as you want (<50GB)

---

### Post by fcomstoc on 2011-08-17
or set windows to a smaller partition in the setup

---

### Post by n213978745 on 2011-08-17
If I remember correctly, the reason why you can only shrink half of NTFS partition, is because NTFS puts the metadata right in the middle of the partition.

Even though you only use like 50 GB out of 1TB for Windows partition, they only let your shrink half of it.

Yes, you can use gparted to force shrinking, but you will need Windows Recovery Disc to "check error" or fix it after.  I had tried it myself before on Windows Vista.


I will suggest you to just reinstalling the Windows on a pre-defined size.

---

### Post by TE7 on 2011-08-17
If I use G-Parted, will the Windows repair disc work?

---

### Post by westie457 on 2011-08-17
> **TE7 said:**
> If I use G-Parted, will the Windows repair disc work?

Hi.

By all means use Gparted to shrink your Windows partition to any size you want eg 100GB. Gparted will automatically mark that partition to be checked by Windows.

When shrinking or enlarging a Windows partition it is best to move the end-point and leave the start-point where it is.

Also Gparted will not allow any more adjustments to that partition until you have booted into Windows. 

The Windows CHKDSK should run automatically as the OS reports a size difference to what it was used to.

You should not need to use a repair disc if it is only the end-point that gets moved.

---

### Post by Frogs Hair on 2011-08-17
I have  used this method . [http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/](http://www.nirmaltv.com/2009/05/12/how-to-resize-disk-partition-in-windows-7/)

---

### Post by oldfred on 2011-08-17
Make sure you are using a recent gparted. Some older one's (about 2 years ago) also moved the start of the Windows partition to sector 63 which was where XP started. Then you did have to run the Windows repair CD to fix it. It should work now but best to have good backups, have repair CD and be repaired to reinstall as last resort. But it is always best to have all those preparations for any major system changes.

After shrinking with gparted, reboot into windows a couple of times so it can run chkdsk and make any repairs it seems to want to make. Only if chkdsk does not run correctly may you need repair CD.

---

### Post by TE7 on 2011-08-17
Thanks for the info guys. I'll try GParted and report back, that is if I can get back online afterwards.

---

### Post by overdrank on 2011-08-17
Moved to General Help

---

### Post by TE7 on 2011-08-17
GParted worked great. I was able to shrink my Windows 7 64 bit boot (primary) partition from 468 GB to 100 GB. Just some things I did that I gleaned from the web:

1) In Windows 7, I disabled the following first:

       - System Protection (System Restore)
       - Virtual Memory (No page file)
       - Hibernation (Sleep)

I did this because these features are associated with being unmovable files, and I didn't want Windows to get confused the next time it booted. I turned them back on after I was done.

2) I didn't move the beginning of the Windows partition (left the space before the partition to 0) when using GParted. I just created space after the partition.

Thanks for the input guys.

---

