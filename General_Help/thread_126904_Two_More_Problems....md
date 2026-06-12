---
title: "Two More Problems..."
date: 2006-02-07
forum: General Help
---

### Post by xMist on 2006-02-07
Hey guys...

I've got two pressing problems here:

1. How the heck do I uninstall ndiswrapper?  I've installed it, but on entering modprobe ndiswrapper, it tells me that the operation is, um, I forget...something to do with security, I think.  Oh!  It says operation not permitted.  The reason I'm looking to uninstall it is because if I get a fatal error, I should uninstall the version that came with Ubuntu first.  It says to use 'make uninstall', but I have no idea what to do with that.

2. I've got two hard drives in my computer: an 80GB and a 20GB.  XP is on the 80, Ubuntu on the 20.  The 80 is formatted with NTFS, the 20 with FAT32.  However, each operating system can only see its own drive, and not the other.  Is there any way I can get them to recognize the other?  Even if it's only one way, it would help.  Thanks!

-Bobby

---

### Post by taurus on 2006-02-07
1.  How did you install ndiswrapper?  If you installed with synaptic (i.e, apt-get), then you can use it to remove it.  But if you built it from source, then you need to get into the directory where you built it and run that command, make uninstall, to remove it...

2.  Assuming your XP is on /dev/hda1 and your fat32 is on /dev/hda2, do

sudo mkdir /mnt/xp /mnt/fat32
sudo mount -t ntfs /dev/hda1 /mnt/xp
sudo mount -t vfat /dev/hda2 /mnt/fat32

---

### Post by xMist on 2006-02-07
Thanks for all your help so far.  I've completed your answer to number 2.  My hard drives are actually listed as the Ubuntu 20 - hdb1 and XP 80 - hda1.  It mounts my XP without a hitch, but I don't know how to access it.  I went into a /mnt/ folder, and tried to open the /mnt/xp/ folder, but it tells me I don't have sufficient priveleges.  I'm not quite sure what that means.  For the mounting of hdb1, it says that it's already mounted or busy, which is true, because Linux is running off of it and I already have complete access to it.  If you don't mind, I have two more questions:

-Is there some script I can make into a 'shortcut' of sorts on my desktop so this can be performed easily?  (also with the mounting of my floppy)
-Is there a way I can get Windows to recognize my 20GB hard drive that is not formatted under FAT32?  This would make it much easier to share files between the two.

I'll let you know as soon as I have tried your answer to #1 above.  Thanks again!

---

### Post by aysiu on 2006-02-07
[QUOTE=xMist]
2. I've got two hard drives in my computer: an 80GB and a 20GB.  XP is on the 80, Ubuntu on the 20.  The 80 is formatted with NTFS, the 20 with FAT32.  However, each operating system can only see its own drive, and not the other.  Is there any way I can get them to recognize the other?  Even if it's only one way, it would help.  Thanks![/QUOTE] You installed Ubuntu on FAT32? Not a good idea. The best thing to do is make Windows NTFS, Ubuntu Ext3, and a separate FAT32 partition to share between the two.

---

### Post by xMist on 2006-02-07
Wait, now I'm confused.  I thought it would be best, since I have two different hard drives, to use each for a different operating system?

Or are you saying that I should've formatted the second 20GB HDD as NTFS?  Oops.  So, I should've formatted the 20GB with two partitions, as in like a 15GB NTFS for Ubuntu, a 5GB for sharing?  Why would I need a FAT32 partition at all, then?  Windows can read NTFS just fine...I have a feeling I"m missing something ;)

---

### Post by RAOF on 2006-02-07
You're right, a separate hard drive for each OS is a fine idea.  You haven't installed Ubuntu onto a FAT32 partition, though.  The install process would have formatted that partition (probably to EXT3).  It is not actually possible to install Ubuntu on a FAT32 filesystem - FAT32 is just too primitive.

To access your Ubuntu partition from Windows you can try the ext2 driver from [www.fs-driver.org](www.fs-driver.org).  To access (read access only) your Windows partition from Ubuntu, try the "Accessing windows drives" link in my sig.

---

### Post by xMist on 2006-02-07
Thanks, RAOF.  I didn't realize that I hadn't formatted it as a FAT32 partition.   I guess it was that before I installed Ubuntu on it, but the Ubuntu partition(er) must have fixed that for me.  The link to fs-driver.org helped - I can now see files from Ubuntu!! yayy!

As soon as I boot into Ubuntu again, I'll try the link from your singature.  Thanks.

---

### Post by xMist on 2006-02-07
I have just one problem - the part of your signature that I went to requested a script file to be downloaded.  I can't do that because I don't have my WUSB54G set up yet (that's another problem.)  Is there any way I can save the text at the address that it sends me to ([http://www.ubuntulinux.nl/files/diskmounter](http://www.ubuntulinux.nl/files/diskmounter)) and use it from that file?  Thanks...

---

### Post by RAOF on 2006-02-07
You could just copy the text to a text file using copy/paste.  The script is nothing but that text.  Just save it to a text file, chmod +x <filename>, and then run it with ./<filename>

Or you could follow the instructions further down the page - they deal with setting it up manually, without using that script.

---

