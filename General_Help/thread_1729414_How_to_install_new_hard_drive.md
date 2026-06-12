---
title: "How to install new hard drive"
date: 2011-04-14
forum: General Help
---

### Post by yc2 on 2011-04-14
Hello,

From long ago I think I remember that, in order to install a new hard disk, I must:
1. create a mountpoint (mkdir ...)
2. enter one line (for each partition) in /etc/fstab

Is it still like this, or has this become automatic so that a new (common, internal IDE) disk will be automatically mounted without manually editing fstab?

Thank you.

---

### Post by yetiman64 on 2011-04-14
> **yc2 said:**
> Hello,

From long ago I think I remember that, in order to install a new hard disk, I must:
1. create a mountpoint (mkdir ...)
2. enter one line (for each partition) in /etc/fstab

Is it still like this, or has this become automatic so that a new (common, internal IDE) disk will be automatically mounted without manually editing fstab?

Thank you.

Listing a disk partition in /etc/fstab is for automatically mounting the partition at startup, do you need to do that? If not any new drive plugged in should be available to nautilus in Places > Removable Media. Just click on it here to open it to a nautilus window.

Edit: the mounting of removable drives is done with /etc/mtab, whereas permanent mounting is done with /etc/fstab.

---

### Post by papibe on 2011-04-14
The drive may be already formated on FAT or NTFS, so it maybe get mounted automatically the first time you boot after the physical install.

After that, you can use System -> Administration -> Disk Utility to unmount and format the drive (either ext3 or ext4).

If it's not automounted you can jump directly to the Disk Utility, or in the case you need to divide the disk into more partitions you can use Gparted (like in this [tutorial]("https://help.ubuntu.com/community/InstallingANewHardDrive"))

Of course, you can always go the terminal way and use fdisk (only way if you have a server). This is a good [guide ]("https://help.ubuntu.com/community/InstallingANewHardDrive")to do that.

I hope it helps.

---

### Post by yc2 on 2011-04-14
Thanks guys. I see now that I didn't ask clearly. My question should have been like this:

I have an Ubuntu system that is already installed and has run for some time. I now buy a new IDE disk where I already have a filesystem.

If I just turn off my box, introduce the disk physically into the computer, will this disk become mounted automatically every time the system starts?

As I understand yetiman64, any partiton available to the system will be available and mounted if I click it under the menu places? (But you also mention "removable media". Does an IDE disk list under removable media?)

---

### Post by yetiman64 on 2011-04-14
> **yc2 said:**
> ... Does an IDE disk list under removable media?)
 
I suspect it will be accessible in Places > Removable Media & if clicked on there it is then mounted (using the entry in /etc/mtab). Note even NTFS and FAT drives should be listed here.

Even though they are available in Removable Media does not mean they are actually mounted (that is to /media/Foldername). If you list an entry in /etc/fstab they will be mounted how you specify permanently.

---

### Post by papibe on 2011-04-14
> **yc2 said:**
> ...As I understand yetiman64, any partiton available to the system will be available and mounted if I click it under the menu places? 
Yes, yetiman64 is right.
You can also click on Places -> Computer and see it there.

Regards.

---

### Post by yc2 on 2011-04-14
OK, I get it.

To be mounted at system start it must be in fstab.
Otherwise you can still see the device under menu "places" but you have to click it to have the fs mounted.

Thanks for help, I mark this as solved now.

---

