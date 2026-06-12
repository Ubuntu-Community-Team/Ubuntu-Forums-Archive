---
title: "4GB USB Stick Problem!!"
date: 2009-11-23
forum: General Help
---

### Post by xeno_phile on 2009-11-23
Hi, i bought a Maxell 4GB Venture USB stick today, when i plugged it in i got a strange result.
Looked at it in GParted and this is what i get...
> 
[B]Device Imformation
Model: [/B]USB DISK Pro
**Size:   **0.00B
**Path:**  /dev/sdc

**DiskLabelType: **unrecognized
**Heads:**               255
**Sectors/Track:  **63
**Cylinders:          **0
**Total Sectors:  **0The Partition showing in GParted is unallocated, size 512.00B!!!!
Obviosly something is not quite right.
Thought i would ask if there is anything i can try before i take it back and exchange it tomorrow. 

xeno_phile

---

### Post by philinux on 2009-11-23
Not sure but it might have the usb U3 software on it.

[http://www.mydigitallife.info/2006/09/11/disable-remove-and-uninstall-u3-launchpad/](http://www.mydigitallife.info/2006/09/11/disable-remove-and-uninstall-u3-launchpad/)

---

### Post by efflandt on 2009-11-23
It looks like someone may have either wiped that clean or it is defective.  Most already have a partion on them that Windows can use.

What does **sudo fdisk -l** show for it?  This is an example of a 4 GB HP USB stick, but your sd device and heads, cyl may vary.

```
Disk /dev/sdf: 4009 MB, 4009754624 bytes
124 heads, 62 sectors/track, 1018 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x0005e586

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        1018     3913161    c  W95 FAT32 (LBA)
```You might try using gparted to create an msdos "partion table" on it and then add a vfat (FAT32) partition.  But if that does not work, there may be something wrong with it (had the package been opened?).

PS: If it does have U3 on it, that also has a pseudo sr device mounted as a cdrom even if you totally wipe and repartition it (apparently in ROM).  And that would greatly extend (double) the boot time if trying to use it for bootable live/install iso.

---

### Post by xeno_phile on 2009-11-23
Result from fdisk...
> xeno@work ~ $ sudo fdisk -l /dev/sdc

Disk /dev/sdc: 1 MB, 1048576 bytes
1 heads, 2 sectors/track, 1024 cylinders
Units = cylinders of 2 * 512 = 1024 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table Package was as new. Fully sealed.
Creating "msdos partition table" just changes the 512.00B to  **-**(minus)[B]512.00B!!
[/B]

---

### Post by khelben1979 on 2009-11-23
> **xeno_phile said:**
> Result from fdisk...
Package was as new. Fully sealed.
Creating "msdos partition table" just changes the 512.00B to  **-**(minus)[B]512.00B!!
[/B]

Do you have the possibility on testing if it works okay on a Windows system? If it doesn't, it's definitely faulty.

---

### Post by xeno_phile on 2009-11-23
A Windows Box recognised it as a USB Device, but when i try to open it Windows says that location is empty. Windows won't format it either. 
Maxell Venture is a bussiness class USB device, it should contain Lock software and other security programs. I've got nothing. I guess it is corrupted. 

xeno_phile

---

### Post by philinux on 2009-11-23
> **xeno_phile said:**
> A Windows Box recognised it as a USB Device, but when i try to open it Windows says that location is empty. Windows won't format it either. 
Maxell Venture is a bussiness class USB device, it should contain Lock software and other security programs. I've got nothing. I guess it is corrupted. 

xeno_phile


Sounds like a duffer.

---

### Post by xeno_phile on 2009-11-23
A Duffer indeed.
I'll exchange it tomorrow.

Thanks for the swift and courteous replies guys, it was much appreciated.

xeno_phile

---

### Post by tesseract_rider on 2010-01-15
A quick search produced this:
>  I have a Venture USB and am experiencing partition problems with Windows Vista, what shall I do?

Venture USB contain two partitions - one named 'Public' and the other 'Secure'. Unfortunately we have noticed a compatibility problem between these drives and some computers running Windows Vista. In these cases only one drive is showing in 'My Computer' - usually the 'Secure' drive. As a result you are unable to access the user manuals and software which are in the 'Public' drive and cannot alter the partition sizes to allow access to the entire capacity. 

Please follow the below instructions to resolve the problem:

1. Connect the USB to the computer
2. Please unzip and run the attached program
3. After completion please unplug the USB
4. Re-insert the USB to the USB port
5. You should now be able to access both drives.

Please [_click here_]("http://www.maxell.eu/DriverDownloads/Close.rar") to download the program and instructions

[http://www.maxell.eu/FAQ2/FAQ.html]("http://www.maxell.eu/FAQ2/FAQ.html")



I was having identical problems under vista, and now all works perfectly. I can re-size the partitions using the enclosed software, but it will be interesting to see what happens when I plug it into my ubuntu box when I get home (in a few months)

---

### Post by ricsi-pontaz on 2010-01-20
> **tesseract_rider said:**
> A quick search produced this:


[http://www.maxell.eu/FAQ2/FAQ.html]("http://www.maxell.eu/FAQ2/FAQ.html")



I was having identical problems under vista, and now all works perfectly. I can re-size the partitions using the enclosed software, but it will be interesting to see what happens when I plug it into my ubuntu box when I get home (in a few months)

Hi! I have got the same pendrive. But unfortunately i deleted the pendrive software and can't find on the internet. Can you send me?

---

### Post by burgersnchips on 2010-03-05
Hello

Sorry bump an old thread, just thought I'd mention that I've recently had one of these memory pens and I have the software provided with the device and also the software required to turn it into a regular single drive memory pen, although I'm unsure about Linux compatibility as I actually run Windows. You may need to get XP going in a Virtualbox or something.

Anyway, the software provided on my memory pen has been uploaded here:
[http://dl.dropbox.com/u/927778/Maxell%20Drive%20Application.zip](http://dl.dropbox.com/u/927778/Maxell%20Drive%20Application.zip)

And the software to convert the memory pen to a regular one is here:
[http://dl.dropbox.com/u/927778/Maxell%20Mode%20Converter.zip](http://dl.dropbox.com/u/927778/Maxell%20Mode%20Converter.zip)

Instructions for use of conversion software:
1. Plug in USB Memory pen
2. Unzip and run conversion software
- A screen will pop up with some options
3. Select "1" under the option "Number of partitions"
4. Press convert
5. The application will ask the user to unplug the memory pen and reinsert, do this.
- The memory pen should now be one partition.

I hope I didn't break any rules posting those links etc, if I did, sorry!

BnC

---

### Post by pat da punk on 2010-05-26
Been looking everywhere on the net to find the programs for this stick!
You star 
thanx         pat:guitar::P

---

### Post by twa14 on 2011-08-26
Thanks for the links to the programs, problem had been driving me crazy for hours!
 
twa14

---

