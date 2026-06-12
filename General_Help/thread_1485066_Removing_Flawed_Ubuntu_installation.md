---
title: "Removing Flawed Ubuntu installation"
date: 2010-05-16
forum: General Help
---

### Post by sedulius on 2010-05-16
I attempted to install ubuntu for the first time. I was installing it as a seperate partition, with Windows 7 as the primary partition.

However, the copy I had made of ubuntu 10.04 was flawed (used a wiped CD-RW, should probably use a basic CD next time), and the installation stopped partway through with no further actions.

So, now I'm wondering how to remove this flawed partition and restore it to Windows 7's partition. The Live CD does work, even though the actual installation was flawed, and I have my installation CD for Windows 7. I've looked on other parts of the forum and have seen I need as much, but there is no solution to this problem I have found that is up to date for Windows 7/ubuntu 10.04.

Also, an odd glitch due to all of this is that my desktop on Windows 7 is now inoperable. The start menu works, the desktop wallpaper shows, everything works, save for actual desktop functions. All icons are missing, though the files are still in the desktop folder, and the mouse cursor cannot make a loop around anything, though it can still right click. It's not a terrible problem, just a little annoying.

---

### Post by mikewhatever on 2010-05-16
Can you boot the live cd and post the output of **sudo fdisk -l** from Applications-Accessories->Terminal. Generally speaking, removing an installation of any operating system is just the matter of deleting the partition it is installed on. You should be able to do it with Gparted from the very same live cd.

---

### Post by sedulius on 2010-05-16
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf264f264

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       48572   390149975    7  HPFS/NTFS
/dev/sda2           48572       60802    98236417    5  Extended
/dev/sda5           48572       60299    94195712   83  Linux
/dev/sda6           60299       60802     4039680   82  Linux swap / Solaris

-----

That was the result.

On a side note, I fixed the side effect. I feel quite silly actually. All I had to do was right click and select show desktop icons. So there was no real error there, just some oddity.

Well, I shall await instruction on the main issue.

EDIT:

Okay, so I didn't wait. I used Gparted, which I found surprisingly simple. No problems. No errors. Everything is back to how it was.

I was worried there would be a boot problem as I've seen in other threads, but Windows automatically performed CHKDISK upon reboot and found no errors. So it all worked out great.

This makes me less afraid to try installing Ubuntu again. I liked working with it.

---

### Post by mikewhatever on 2010-05-16
Well, as said above, all you need to do to remove Ubuntu, is boot from the live cd, open SystemAdmin->Gparted and delete the extended partition identified as /dev/sda2.

---

