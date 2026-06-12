---
title: "How do I create an nfts partition with gpart?"
date: 2011-01-01
forum: General Help
---

### Post by coolbuntukid on 2011-01-01
dell inspiron 1501. super old laptop was running horribly so I installed ubuntu on the entire 80gb harddrive. I have windows 7 pro 32 bit on a usb and wanna install. I tried and it said windows 7 could not install on disk 0 and I need a nfts partition. I installed gparted but can't figure out how to do it. I want 40gb for windows 7. do I create a partition table? it says my entire drive will be formatted if I do that and I don't wanna lose ubuntu.

edit: by the way, I'm borderline retarded when it comes to computers so I need super noob friendly advice.

---

### Post by ajgreeny on 2011-01-01
You can not use gparted from a running ubuntu to do anything to the ubuntu partition as it must be unmounted to work on it, impossible if you're using it.

You need to run the live ubuntu CD (or usb) that you used to install ubuntu, which has gparted on it.  Just make sure nothing on the hard disk is mounted by right clicking on the partitions if needed, and then you can shrink the ubuntu, and make a new ntfs in the free space.

After installing windows you will have to restore grub2, as windows will have put the usual windows bootloader on the disk.  It's easy to do;  see_ [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)_[URL="http://ubuntuforums.org/showthread.php?t=224351"]
[/URL]

---

### Post by kherring7383 on 2011-01-01
It seems the best way, is to boot from a live Gparted CD and resize the exiting partition.
Once that's done, apply all changes to resize the partition. After, click on the newly created partition and choose to format as NTFS, then apply. This should do it.

---

### Post by sgosnell on 2011-01-01
Where do you want to install Windows?  On a USB drive or your internal HDD?  If you want to install on your HDD, you need to boot from a liveUSB image, then run gparted and partition the HDD as you want.  You need to make the first partition as ntfs, because Windows (at least earlier versions, I'm not sure about Win7) will only work on the first primary partition.  Linux will happily go anywhere.  You'll need to drag the left edge of the current partition to the right to make empty unallocated space for the Windows install, format the unallocated space as ntfs, and then exit.  Keep in mind nothing is done until you click on the Apply button, the green checkmark.  It will take awhile to move all the current Linux files to the new partition area.  After it's all done, exit gparted, shut down the computer, connect the USB drive with Windows, and boot from it.  It should install Windows for you.  Now you need to reinstall grub if you want to continue to use Ubuntu.  There are lots of threads on doing this, as well as wiki articles.

---

### Post by perspectoff on 2011-01-01
Yes, you can use GParted from a recent Ubuntu LiveCD (or can use the GParted LiveCD as already recommended).

There is an option to create an NTFS partition within GParted from any existing free space. Obviously this implies you have some free space, so that means you will have to shrink your Ubuntu partition first, creating free space.

Windows likes its partitions at the beginning of the hard disk (in the first and second primary partitions) because its installer assumes that is where they are going to be. 

However, be aware that Windows 7 uses two primary partitions, because it creates its own boot partition in the first primary partition and then installs the Windows OS into the second primary partition. 

My advice is to create 40 Gb of free space at the beginning of the hard drive (using GParted); make sure the Ubuntu OS is pushed to the end of the hard drive, leaving all the free space at the beginning of the hard drive. (This can be done with GParted as well.)

There cannot be more than two partitions already existing on your hard drive if you wish the Windows installer to work. This means you must either have only one or two primary partitions, or one primary and one extended partition on the hard drive (and the rest is free space, as described).

Then allow the Windows installer to create its own NTFS partitions in the free space as part of its own installation process. This is going to be the least stress for you.

Windows will overwrite the MBR (Master Boot Record) to refer to its own bootloader only, so after Windows is completely installed, you will later have to reset the MBR to refer to Grub2 once again. Those instructions are posted many times elsewhere and can be re-posted in a separate reply.

In general you would use

 grub-install -v 

from an Ubuntu LiveCD or

 sudo grub-install /dev/sda

---

### Post by wilee-nilee on 2011-01-01
> **ajgreeny said:**
> You can not use gparted from a running ubuntu to do anything to the ubuntu partition as it must be unmounted to work on it, impossible if you're using it.

You need to run the live ubuntu CD (or usb) that you used to install ubuntu, which has gparted on it.  Just make sure nothing on the hard disk is mounted by right clicking on the partitions if needed, and then you can shrink the ubuntu, and make a new ntfs in the free space.

After installing windows you will have to restore grub2, as windows will have put the usual windows bootloader on the disk.  It's easy to do;  see_ [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)_[URL="http://ubuntuforums.org/showthread.php?t=224351"]
[/URL]

+1

Windows needing to be in the first primary is not true, follow this advice, make sure you right click the new NTFS in gparted then flags click boot=active partition before installing. The partition has to be active for the W7 installer to see it.

---

### Post by perspectoff on 2011-01-01
> **wilee-nilee said:**
> +1

Windows needing to be in the first primary is not true, follow this advice, make sure you right click the new NTFS in gparted then flags click boot=active partition before installing. The partition has to be active for the W7 installer to see it.

Thank you. I stand corrected. I forgot about the boot flag. When Windows 7 creates two partitions, a boot partition and an OS partition, which one has the boot flag set?

---

