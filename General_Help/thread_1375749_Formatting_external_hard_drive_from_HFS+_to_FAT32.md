---
title: "Formatting external hard drive from HFS+ to FAT32"
date: 2010-01-08
forum: General Help
---

### Post by carlrac on 2010-01-08
I recently bought a Western Digital 'my passport' 500Gb external hard drive for use on my mac and PC. Basically i want to use it for Linux, Windows and OSX but the drive came pre-formatted in HFS+ for some stupid reason. Obviously the solution is to reformat to FAT32 since i don't need to store any large .iso or high def video files on the drive.

Unfortunately windows wont recognise it properly and my mac wont let me format it anything other than the variants of MacOS Extended and MS-DOS, so of course i've turned to Ubuntu (specifically Mint) for a solution. Does anyone have any experience doing anything like this? Also after a little research, i'm assuming it's possible since it can read HFS+ and has formatting utilities, but do tell me if it isn't possible! I'm relatively new to Linux, so any advice on how to go about doing this would be greatly appreciated :)

Thanks!

---

### Post by Cabs21 on 2010-01-08
Use Gparted and format it to what ever you want.  Gparted is light and efficient.

Just did this to my 'WD' 500 GB protable HD and it worked perfectly fine.

---

### Post by barnex on 2010-01-08
If I'm not mistaking, MS-DOS just means FAT, so you can probably format it under macosx. Just give it a try. Anyhow, after that windows should recognize it and allow you to reformat again if necessary.

---

### Post by audiomick on 2010-01-08
Hallo.
You can get a gparted (partitioning tool) live CD here
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
boot from it and do it from there,

or install (if it isn't already there) gparted into your Ubuntu system, run it (turns up in system> administration on Ubuntu) and do it from there.

From the terminal
```
sudo apt-get install gparted
```should install

to run```

gksu gparted
```

This applies to Ubuntu. I don't know if there are any differences in Mint.

---

### Post by anaconda on 2010-01-08
I wouldn't use fat32 because of its limits  (4 GB file size limit and no access rights, and the most annoying one: ubuntu wont know which files are executables, and so it will be asked each time you doubleclick a .txt file... do you want to execute or display it...) 

Have you considered ext3 of ntfs?

ntfs works with ubuntu, and there is an ext3-driver for windows

I dont know about macOS, but I assume macs can read and write to ntfs and ext3..

---

### Post by carlrac on 2010-01-08
Thanks everyone, i'll give Gparted a try!

> **anaconda said:**
> I dont know about macOS, but I assume macs can read and write to ntfs and ext3..

Nope NTFS is read only on Mac. There are programs to overcome this, but apparently it's very slow

> **barnex said:**
> If I'm not mistaking, MS-DOS just means FAT, so you can probably format it under macosx. Just give it a try. Anyhow, after that windows should recognize it and allow you to reformat again if necessary.

Yeah i was gonna try the MS-DOS option and use windows to format it but windows wont format anything larger than 32Gb to FAT32. Still unsure of the distinction between MS-DOS and FAT, but that's irrelevant if formatting in linux works

---

### Post by Bernard_ivo on 2010-01-12
Any idea why after using Gparted to format to ext3/4 from HFS+ I lost 23 GiB and my 500G HDD (My Passport Studio) is now only 434 GiB free to use. I know that 500GiB is advertised only, but under HFS+ I had 465 GiB free to use. Under Ubuntu the HD has 458 GiB total capacity and after formating it went down to 434. 
Formatting to NTFS worked - 465 GiB free, though it is not Linux file-system anymore 

Cheers

---

### Post by Leppie on 2010-01-12
> **carlrac said:**
> Yeah i was gonna try the MS-DOS option and use windows to format it but windows wont format anything larger than 32Gb to FAT32. Still unsure of the distinction between MS-DOS and FAT, but that's irrelevant if formatting in linux works

the ms-dos option you are presented in osx is fat32 which has a limit of 32gb per partition, see here: [http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)

the discrepancy in available space is due to root reservation.
you can change it by using the "tune2fs -m" command

---

### Post by kenox on 2010-01-12
In linux first partition the disk(if required) using fdisk ```
sudo fdisk /dev/<name of disk>
```

Then run ```
sudo mkfs.vfat /dev/<name of device>#
```
the # represents the partition number eg sudo mkfs.vfat /dev/sda1

I dont know about making 500gb fat32 partitions.. i would say try it and then test it before use!!

---

### Post by Cabs21 on 2010-01-12
> **Leppie said:**
> the ms-dos option you are presented in osx is fat32 which has a limit of 32gb per partition, see here: [http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)

That 32 GB limit is set by Microsoft to increase the use of NTFS formatting in windows.  If you are planing on only using the external as a data storage unit across multiple Operating Systems then I would say use FAT32.  It can be read and written on in may OSs and yes you would have to tell a text file to open instead of run but that is only if you click the text file.  If you open OpenOffice and open the file from there it will not ask it will just open.

---

### Post by carlrac on 2010-01-16
Ok i finally got around to doing this and i thought it was as simple as right click->format

Only thing is i keep getting this error message:
"Error creating file system: helper exited with exit code 1: helper failed with: Total number of sectors (975138736) not a multiple of sectors per track (63(! Add mtools_skip_check=1 to your .mtoolsrc file to skip this test"

Couldn't find this file so i tried gparted like suggested, but it only ran for a minute or two then it was finished. But when i plugged it into my PC and Mac, neither could recognise it :(

Does anybody know what happened here? As i said, i'm new to linux, but i hope i havn't made things worse... Also, shouldn't formatting take much longer than just a couple of minutes for 500Gb (well 465Gb really!)

---

