---
title: "&quot;Properly&quot; preserving files when resizing partition?"
date: 2011-10-13
forum: General Help
---

### Post by IQAndreas on 2011-10-13
I'm about to expand my current partition (on the same harddrive) from 10GB to 20GB. This is my plan:

[LIST]
[*]Boot into a LiveCD
[*]Copy all files from my current Ubuntu installation in partition A to an external harddrive
[*]Resize (or merge with another, actually) partition A to the new size (20GB)
[*]Copy all files back from the external USB to my new 20GB partition
[*]Boot back into my Ubuntu installation, and enjoy the extra space
[/LIST]

My question is, will this work, and the Ubuntu run properly?

Or are there files/settings/data that are hidden "elsewhere" than as physical and copy-able "files"?

Or perhaps settings that depend on the fact that the partition *should* still be 10GBs in size?

---

### Post by varunendra on 2011-10-14
> **IqAndreas said:**
> I'm about to expand my current partition (on the same harddrive) from 10GB to 20GB. This is my plan:

[LIST]
[*]Boot into a LiveCD
[*]Copy all files from my current Ubuntu installation in partition A to an external harddrive
[*]Resize (or merge with another, actually) partition A to the new size (20GB)
[*]Copy all files back from the external USB to my new 20GB partition
[*]Boot back into my Ubuntu installation, and enjoy the extra space
[/LIST]

Nothing seems wrong with your plan, just make sure a few things:

[LIST]
[*]Instead of trying 'merger' (since it may be confusing), simply 'Resize' your partition. This will make sure its partition number and UUID stay the same as they currently are. To do so, you may either shrink or delete the 'other' partition (which should be in the 'right' side of the ubuntu partition) towards which you are planning to expand.
[*]While copying, make sure to enable "View Hidden Files" in nautilus (ctrl+h). Since you would be resizing, this is just a precautionary step in case something goes wrong while resizing.
[/LIST]
To be extra safe, you can use clonezilla to make an image of the ubuntu partition, then restore it on the expanded one. In any case, if the the partition number (or its UUID in some cases) changed during the operation, then you may also have to reinstall GRUB from the CD (which is a very easy step, if required at all).


To precisely answer your questions-
> **IqAndreas said:**
> My question is, will this work, and the Ubuntu run properly?Yes, this 'should' work without issues.

> **IqAndreas said:**
> Or are there files/settings/data that are hidden "elsewhere" than as physical and copy-able "files"?Many of them 'ARE' hidden, but not "elsewhere" unless you have intentionally created separate partitions like /, /boot, /home, etc. So make sure to enable the "View Hidden Files" option, and you are good to go. The only thing related with installation that you cannot copy normally is the MBR (GRUB - for Ubuntu) itself. But it is easy to reinstall in case the partition info gets changed.

> **IqAndreas said:**
> Or perhaps settings that depend on the fact that the partition *should* still be 10GBs in size?There is no such restriction as long as the boot sector and the files are intact.

---

### Post by dcstar on 2011-10-14
> **IqAndreas said:**
> I'm about to expand my current partition (on the same harddrive) from 10GB to 20GB. This is my plan:
.........

If you have 20GB of free space on the drive, just use a LIVE CD/USB and **gparted** to "copy and paste" the existing Ubuntu partition to that area.

Change the new partition's UUID (search for detailed instructions), then reboot into Ubuntu and do:

```
sudo update-grub
```

Mount the new partition and change the /etc/fstab file in it to use the new UUID.

Reboot into the new 20GB Ubuntu system, then:

```
sudo dpkg-reconfigure grub-pc
```
And install the boot loader.

Now you will be booting Grub off the new Ubuntu partition and you can now delete the old 10GB partition.

---

### Post by IQAndreas on 2011-11-03
Thanks for the help guys.

My partitions were set up as follows:
[FONT="Courier New"][ --- Windows 60GB partition --- ][ - Ubuntu 10GB part - ][ - No longer used 10GB part - ][/FONT]

All I had to do was delete the third partition, and resize the Ubuntu partition to 20GB (using GParted from a LiveCD).

No files were deleted or needed to by copied and pasted after the Ubuntu partition had been resized. (but it's always a good idea to make a backup before anyway)

---

