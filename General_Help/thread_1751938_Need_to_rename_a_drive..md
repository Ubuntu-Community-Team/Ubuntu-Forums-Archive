---
title: "Need to rename a drive."
date: 2011-05-07
forum: General Help
---

### Post by Zortis on 2011-05-07
I installed Ubuntu, C: drive became E:

I need someone to tell me how to change E: back to C: and nothing else.

I don't have access to Windows - this is only doable on the Ubuntu live CD.

---

### Post by Zortis on 2011-05-07
.

---

### Post by VCoolio on 2011-05-07
What makes you think C: became E: ? It's not ubuntu that did that; and from an ubuntu live cd you can't change it. C: or E: is windows terminology. Linux uses /dev/sdaX for partitions. Try a windows recovery cd if you can't boot windows anymore. You may have to reinstall grub afterwards to reach ubuntu again.

---

### Post by Zortis on 2011-05-07
Sorry to hurt your feelings, Ubuntu fanboy, but Ubuntu did change it.

I would use the Windows repair CD but it looks for C: drives...

---

### Post by edm1 on 2011-05-07
Can you post the results of
> sudo fdisk -l
that will show us how your HD has been partitioned.

Is the problem that you can't boot windows or you cant boot windows or ubuntu?

---

### Post by Zortis on 2011-05-07
Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb11e9751

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       72858   585228027    7  HPFS/NTFS

Disk /dev/sdf: 2051 MB, 2051014656 bytes
64 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1009     2001825    c  W95 FAT32 (LBA)

---

### Post by The Cog on 2011-05-07
C: and E: are windows names for partitions, nothing to do with Linux. 

Is is possible that you created a FAT or NTFS partition while installing, and that windows is now thinking of that new partition as C:? If so, using gparted to change its type to something that windows won't recognise (or just delete it for now) should fix things. 

If that's not it, I cannot think why else installing Ubuntu would make windows decide to allocate different names to the windows-visible partitions (windows can't even see linux partitions).

---

### Post by Zortis on 2011-05-07
I didn't create the partitions I let Ubuntu do it (side by side installation).

And after that Windows became E: 

BUT all of the paths in the programs still look for C:

---

### Post by edm1 on 2011-05-07
> **Zortis said:**
> Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb11e9751

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       72858   585228027    7  HPFS/NTFS

Disk /dev/sdf: 2051 MB, 2051014656 bytes
64 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 3968 * 512 = 2031616 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1009     2001825    c  W95 FAT32 (LBA)

Ah, you are currently running off the live CD. Can you explain what the actual problem you are experiencing and wanting to fix is. How do you know that windows sees C: as having changed to E: if you cant access it? What operating system can you access at the moment. What is preventing you starting the others? When you installed Ubuntu what options did you select for partitioning your HD (use entire disk, resize disk, manual)? What filesystems did you chose to use?

---

### Post by Zortis on 2011-05-07
Oh and I removed Ubuntu from my computer so that removed the bootloader, now because there's no bootloader Windows can't boot and because Windows is E: and the repair CD only looks for C: I can't fix that...

---

### Post by The Cog on 2011-05-07
OK, you posted your fdisk -l while I was typing my last post.

I see that you have a single partition on sda2, and this is NTFS. I would expect that windows would always call this C:. 

But you do have a 2G sdf (a memory stick perhaps) where sdf1 is formatted FAT. Maybe this is what is being called C: by windows. Try booting windows without the stick plugged it, and see if that fixes things.

---

### Post by edm1 on 2011-05-07
> **Zortis said:**
> Oh and I removed Ubuntu from my computer so that removed the bootloader, now because there's no bootloader Windows can't boot and because Windows is E: and the repair CD only looks for C: I can't fix that...

Ah this is easy. [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Or use a windows CD. You are trying to fix the windows MBR.

Edit: ms-sys isnt in the repositories any more. Give me a minute.

---

### Post by Zortis on 2011-05-07
This is what Windows looked like when I could actually boot into it (see picture).

Now there's the problem of fixing the boot process, then fixing the problem of Windows booting from C:

I checked some of the files in my user folder under Windows and all of the filepaths are C: because of this Windows creates a temporary profile which cannot change anything.

---

### Post by edm1 on 2011-05-07
Cant find a better way to do it from the live CD. Did you download the 32-bit or 64-bit live cd? Download and install ms-sys ([32bit]("http://mirror.pnl.gov/ubuntu//pool/universe/m/ms-sys/ms-sys_2.1.0-1_i386.deb") or [64bit]("http://mirror.pnl.gov/ubuntu//pool/universe/m/ms-sys/ms-sys_2.1.0-1_amd64.deb")). Then you should just have to 
> sudo ms-sys -m /dev/sda.

You might actually be better off using a windows CD to fix it if one is available.

---

### Post by Zortis on 2011-05-07
I can't do it with the Windows repair disc because it only looks in C: for Windows...

---

### Post by flemur13013 on 2011-05-07
> **Zortis said:**
> Oh and I removed Ubuntu from my computer so that removed the bootloader, now because there's no bootloader Windows can't boot and because Windows is E: and the repair CD only looks for C: I can't fix that...

Windows can get partition labels confused quite easily when partitions or disk drives are added or changed. The ubuntu installer doesn't help.

Try a non-MS partition manager that has or can create (on a different machine) a boot disk - Easeus (free) or Paragon, etc. (check at download.com) - they can change drive letters with no problem.   If you haven't already backed up your MS install, you can do that with the "copy partition" function in the UB liveCD - or the part-mgr disk - before going further (if you have something to copy to), though it's too late to backup the boot functionality (and if you recover that, restoring from this backup will break it again).

---

### Post by edm1 on 2011-05-07
if my-sys hasnt work then i have another idea as to what could be the problem. Windows always wamts the MBR to be within the first 10000 or something blocks of the HD. It is possible you have not deleted all the partitions created by ubuntu.

From your live CD/USB download gparted (a partition editor). Open it and select sda from the drop down list at the top. Make sure all partitons here are not mounted. Unless you previously had other partitions set up, you want only one (the NTFS one, i think it may be /dev/sda2 in your case) partition so delete all others, move sda2 to the start of your HD and resize it so that it take up the entire disk. Moving and resizing can take a while on a large disk.

---

