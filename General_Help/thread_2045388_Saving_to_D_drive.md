---
title: "Saving to D: drive?"
date: 2012-08-21
forum: General Help
---

### Post by HipKat on 2012-08-21
His files were not deleted or written over. I have the same problem with dual boot Win 7/Ubuntu 12.04

Win 7 is on C: drive. Ubuntu on D: drive, using Wubi to install

If I open Disk Utility, I can see the D: Drive, I click the link for Host and Nautilus opens showing all my files on the D: Drive, which in Windows is where all my photos, Music, videos, etc are. I can open files from Nautilus, etc.

However, the drive does not mount. I can't save to D: drive when I'm in Ubuntu because it doesn't show up in the Save menu.

Running df -h, the output is:


Filesystem      Size  Used Avail Use% Mounted on
/dev/loop0       29G   14G   14G  51% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  944K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  592K  3.9G   1% /run/shm
/dev/sdb1       466G  215G  252G  47% /host

sdb1 is the C: drive, as you can see. The NTFS Partition on the D: Drive is not showing up, which is a 500 GB HDD. That SHOULD be showing up as sdb2

I've scoured the internet trying to find a way to get the D: drive to mount without having to buy an external to move all my files to.

Here's a screenie of Disk Utility

[img]http://i55.photobucket.com/albums/g128/hipkat/Selection_001.png?t=1345522553[/img]

---

### Post by coffeecat on 2012-08-21
I've moved your post to its own thread. Please start your own threads - you are more likely to get attention.

> **HipKat said:**
> 
If I open Disk Utility, I can see the D: Drive, I click the link for Host and Nautilus opens showing all my files on the D: Drive, which in Windows is where all my photos, Music, videos, etc are. I can open files from Nautilus, etc.

However, the drive does not mount.

Yes it is mounted, otherwise Nautilus would not see it. 

> **HipKat said:**
>  I can't save to D: drive when I'm in Ubuntu because it doesn't show up in the Save menu.

Beware thinking with the "D:" drive nomenclature when in Ubuntu. That is a Windows-only convention and can be confusing. In fact your D: "drive" is not a drive; it is a partition. By save menu, I presume you mean the save option in an application such as LibreOffice. If you want to save directly to your host partition (which in this case is your Windows D: ), choose "save" or "save as" from the application File menu, click on "FileSystem" and then open the host folder. Now navigate to where you want to save the file and save it.

If you want this to be less of a fiddle, it is possible to set up symlinks (more-or-less equivalent to Windows shortcuts) in your Ubuntu home folder pointing to folders in your Windows D: partition. If you need help with this, post details of some of the folders that you will be using that are in your host (D: ) partition.

However - saving files directly to your host partition is not really best practice. I'd suggest saving files first to folders in your home folder and then periodically archiving them to your Windows partition.

---

### Post by HipKat on 2012-08-21
Thx, Coffeecat, I kn ow about the nomenclature, I was trying to simplify it so people would understand what I was referring to, and thanks for making a new thread for me.

Everything you said makes sense except one thing; When I try to open a file from host drive, or save a file to host (the "D: drive"), it doesn't show up as an option in a "Save As..." menu.

Actually, what I do is use Disk Utility to open /host, open a file on that partition, then in the left side of a save as menu, it is there as a recent place, and I can browse to the needed folder on /host.... if that makes sense, but i can't create a shortcut to the /host folder and lock it in nautilus so I can just open it up at will

Symlinks will probably be the way to go. Or the devs figure out why this wasn't a problem until 12.04 came out


Edit!!!

found a quick work around. Hit the Superkey, search Host and you can open the folder from there

---

### Post by coffeecat on 2012-08-21
> **HipKat said:**
> Edit!!!

found a quick work around. Hit the Superkey, search Host and you can open the folder from there

Excellent!

But...

> **HipKat said:**
> 
Actually, what I do is use Disk Utility to open /host, open a file on that partition

Disk Utility is primarily a partitioning tool, although you can use it to mount partitions. But you don't need to mount /host - it's mounted already. If it wasn't mounted, Ubuntu wouldn't work. I wonder if something you are doing with Disk Utility is interfering. Don't use Disk Utility. Simply use Nautilus (the file manager) to browse files in an already mounted partition. You can also use Nautilus to mount unmounted partitions, so Disk Utility is superfluous in the situation you describe.

---

### Post by HipKat on 2012-08-21
> **coffeecat said:**
> Excellent!

But...



Disk Utility is primarily a partitioning tool, although you can use it to mount partitions. But you don't need to mount /host - it's mounted already. If it wasn't mounted, Ubuntu wouldn't work. I wonder if something you are doing with Disk Utility is interfering. Don't use Disk Utility. Simply use Nautilus (the file manager) to browse files in an already mounted partition. You can also use Nautilus to mount unmounted partitions, so Disk Utility is superfluous in the situation you describe.


The problem is that when I open Nautilus, even with a Search, Host is nowhere to be found. I can only access it by clicking on the link in the information window for that drive in Disk Utility, as shown in the image in the OP

---

### Post by Mark Phelps on 2012-08-21
Host is a folder -- and would be at the root of the filesystem.  So, you won't see a separate item in Nautilus for host, just a folder.

Are yoy saying that when you point Nautilus to the root of the filesysem ("/"), there is no Host folder?

---

### Post by HipKat on 2012-08-23
> **Mark Phelps said:**
> Host is a folder -- and would be at the root of the filesystem.  So, you won't see a separate item in Nautilus for host, just a folder.

Are yoy saying that when you point Nautilus to the root of the filesysem ("/"), there is no Host folder?

There is, and that's how I access it using Nautilus, but when it comes to saving files with "Save as" there's no way to get to /host

Ironically, using XBMC, I can see that "drive" or partition (/dev/sdb/) as Drive 2 when browsing to file sources, but can't see /dev/sda1/

I think I'm gonna do some serious backing up when I have time and use a great guide I found for dual booting Windows 7/Ubuntu 12.04 with a SSD as boot drive and HDD as the secondary drive, instead of the config I have now with my 2 HDD's

---

### Post by coffeecat on 2012-08-23
> **HipKat said:**
> There is, and that's how I access it using Nautilus, but when it comes to saving files with "Save as" there's no way to get to /host

Yes, there is. I have double-checked this in a Wubi installation and it is as I described in post #2. In brief:

Save/save as -> Highlight "File System" in the left pane of the save window with a single-click -> Look for the host folder in the main pane and open that.

If you are not seeing this, then either you are doing something wrong or something has gone wrong with your installation. As a point of information, the save/save as window is a version of Nautilus.

---

