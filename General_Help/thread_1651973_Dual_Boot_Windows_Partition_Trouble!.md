---
title: "Dual Boot Windows Partition Trouble!"
date: 2010-12-24
forum: General Help
---

### Post by LegitTalon on 2010-12-24
Let me preface this by saying that I've only been a linux user for 13 hours. I love it so far but this dual boot issue is pissing me off. Let me explain.

I first installed Ubuntu 10.10 on to a flash drive and then soon after moved it to dual boot. It took me a few tries to dual boot but eventually I got it, with what I think is bugless success. 

Well anyway, I was able to switch between Ubuntu 10.10 and Windows Vista perfectly fine...up until 2 hours ago. Now only my Ubuntu partition works. and when I try to mount my HP drive I get this error:

```

Error mounting: mount exited with exit code 13: The disk contains an unclean file system (0, 0).
The file system wasn't safely closed on Windows. Fixing.
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.
```

I've tried all the possible safe modes and I've googled everywhere. There were fixes that I found I think would work but I couldn't comprehend the lingo. 

I do not have my windows disk so I think that means I can't chkdsk /f and I have no access to any windows computer, currently. What I need is a fix that I can download and execute or whatever inside of Ubuntu. 

Can someone please help. I'm really hoping I didn't lose all of my windows data. 

Also, this might be useful, here is my "sudo fdisk -l"


```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       75926   609875563+   7  HPFS/NTFS
/dev/sda3           75927       77825    15253717+   7  HPFS/NTFS

Disk /dev/sdb: 32.5 GB, 32462864384 bytes
255 heads, 63 sectors/track, 3946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b6f10

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           1        3947    31699969    5  Extended
/dev/sdb5            3852        3947      761856   82  Linux swap / Solaris
/dev/sdb6               1        1926    15467520   83  Linux
/dev/sdb7            1926        3851    15462400    b  W95 FAT32

Partition table entries are not in disk order
```


[SIZE="5"]P.S. I'm new to this so simplest terms possible would be appreciated. THANKS![/SIZE]

---

### Post by Quackers on 2010-12-24
Have you attempted to change Windows files from within Ubuntu perhaps?

If you have a Windows 7 repair disc you should boot from it. Choose the repair option if you get it, then choose the command prompt.
Enter ```
chkdsk C: /r
``` and hit enter.
If the chkdsk finishes but reports that errors have been fixed you should run it again until no errors are reported.

---

### Post by LegitTalon on 2010-12-24
> **Quackers said:**
> Have you attempted to change Windows files from within Ubuntu perhaps?

If you have a Windows 7 repair disc you should boot from it. Choose the repair option if you get it, then choose the command prompt.
Enter ```
chkdsk C: /r
``` and hit enter.
If the chkdsk finishes but reports that errors have been fixed you should run it again until no errors are reported.

I have Vista and I don't have the disk. :/

---

### Post by Quackers on 2010-12-24
Ah yes, I just re-read the middle bit of your post.
The fact is I don't know of another way to run it. You should download a repair disc - there are plenty of sites that have them - here's one 
[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

For the purposes of this repair Windows Vista and Windows 7 are the same. Be sure to download the same 32 bit/64 bit as your system.

If you have another computer running Vista or Win 7 you can make a repair disc in a few minutes by going to Control Panel > Backup and Restore Centre and looking on the left side click on "make a recovery cd".

---

### Post by wilee-nilee on 2010-12-24
> **LegitTalon said:**
> I have Vista and I don't have the disk. :/

You will now.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by LegitTalon on 2010-12-24
> **wilee-nilee said:**
> You will now.
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

So now how do I use that file with ubuntu to make a disk. Can I use a flash drive instead of a cd?

---

### Post by Quackers on 2010-12-24
Brasero would do it.

---

### Post by LegitTalon on 2010-12-24
> **Quackers said:**
> Brasero would do it.

I seem to be having trouble installing Brasero...

---

### Post by Quackers on 2010-12-24
Brasero is installed by default.
Accessories > Sound & Video > Brasero

---

### Post by LegitTalon on 2010-12-24
If someone could give detailed step by step instructions on how to make a usb bootable of Hirens CD using only Ubuntu I would be very much grateful for that. Keep in mind I don't know Linux at all. :)

---

### Post by LegitTalon on 2010-12-24
> **Quackers said:**
> Brasero is installed by default.
Accessories > Sound & Video > Brasero

Oh...heh. Sorry. I'm like the noobiest of the noobs right now.

---

### Post by Quackers on 2010-12-24
We've all been there :-)

---

### Post by LegitTalon on 2010-12-24
Burning disk now. Though, I think I should have used Hiren's instead of the vista recovery because it would have been more useful and I only have one DVD. 

Hopefully I get the desired results! 

Here we go...

---

### Post by Quackers on 2010-12-24
Burn it as an image! Don't just burn the file!

---

### Post by LegitTalon on 2010-12-24
> **Quackers said:**
> Burn it as an image! Don't just burn the file!

I'm pretty sure I did. How do I use it though?

---

### Post by Quackers on 2010-12-24
You put it in the drive and shut down your system, then start it up again and hopefully your system will boot from it.
You may need to change the first boot device to the cd drive in your bios (if it isn't already set that way).

---

### Post by LegitTalon on 2010-12-24
> **Quackers said:**
> You put it in the drive and shut down your system, then start it up again and hopefully your system will boot from it.
You may need to change the first boot device to the cd drive in your bios (if it isn't already set that way).

Okay so I made the system boot it but when it finally loads I get a black screen with a cursor, that's it. :/

---

### Post by Quackers on 2010-12-24
Well that's not right then.
What dvd did you use? dvd r or rw?

---

### Post by LegitTalon on 2010-12-24
Dvd+r.

---

### Post by LegitTalon on 2010-12-24
Is there anyway I could make a USB bootable version of Hiren's CD using only Ubuntu? There's a tutorial on his site for windows but that obviously doesn't help.

---

### Post by Quackers on 2010-12-24
Unless you've got a cd rw or a dvd rw that you can erase you're struggling then.
I don't know whether Lilo will work or not. See post #3 below
[http://ubuntuforums.org/showthread.php?t=1643408&highlight=lilo](http://ubuntuforums.org/showthread.php?t=1643408&highlight=lilo)

There is a usb method mentioned at the bottom of the link I gave you earlier, but I think you may need Windows to use it.

---

### Post by LegitTalon on 2010-12-24
[https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/8.04/installation-guide/i386/boot-usb-files.html)

Think this will also work? If so how do I find and/or make a partition on my USB.

Thanks for the help by the way. I appreciate it.:D

---

### Post by Quackers on 2010-12-24
I honestly don't know. I suspect that is for an Ubuntu Live usb.

---

### Post by wilee-nilee on 2010-12-24
Hirens is a great disc not sure what you expect it to do.

Here is a .exe loader for a thumb right off their site.
[http://www.hiren.info/pages/bootcd-on-usb-disk](http://www.hiren.info/pages/bootcd-on-usb-disk)

---

### Post by LegitTalon on 2010-12-24
What I'd really like to do is completely remove my linux partition and just have my windows so that I can start all this from scratch. I have to go through all this ****. 

I don't understand Lilo. UGH.

---

### Post by LegitTalon on 2010-12-24
> **wilee-nilee said:**
> Hirens is a great disc not sure what you expect it to do.

Here is a .exe loader for a thumb right off their site.
[http://www.hiren.info/pages/bootcd-on-usb-disk](http://www.hiren.info/pages/bootcd-on-usb-disk)

Can't do much with .exe...

---

### Post by Quackers on 2010-12-24
Have a look at wilee-nilee's link one post above your last.
Don't you know anyone with a Vista or Win 7 system that has a repair disc or can make you one? We're talking about a 5 minute job here and 1 cd. 
In all honesty this is a disc which you could have made at any time since you've had Vista. It's a very worthwhile tool to have.

---

### Post by LegitTalon on 2010-12-24
> **Quackers said:**
> Have a look at wilee-nilee's link one post above your last.
Don't you know anyone with a Vista or Win 7 system that has a repair disc or can make you one? We're talking about a 5 minute job here and 1 cd. 
In all honesty this is a disc which you could have made at any time since you've had Vista. It's a very worthwhile tool to have.

I'm working on having my friend come over. Unfortunately it's 12:58 am here so I might have to wait until tomorrow... :/

---

### Post by Quackers on 2010-12-24
I understand. Has he/she got one? Or can they make one?
Or do they have a Vista/Win 7 installation disc?

---

### Post by LegitTalon on 2010-12-24
> **Quackers said:**
> I understand. Has he/she got one? Or can they make one?
Or do they have a Vista/Win 7 installation disc?

I'd make one with their computer. This is so frustrating. Do you think having a Geek Squad recovery disk would help?

---

### Post by Quackers on 2010-12-24
I'm afraid I don't know what that is :-)

---

