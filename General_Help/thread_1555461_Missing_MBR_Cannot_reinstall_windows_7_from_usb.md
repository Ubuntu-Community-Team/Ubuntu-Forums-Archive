---
title: "Missing MBR: Cannot reinstall windows 7 from usb"
date: 2010-08-18
forum: General Help
---

### Post by peglegtrading on 2010-08-18
Hi everyone,

I made a typical newbie linux mistake and wiped my hard drive completely when installing Ubuntu. Now I need to access Windows 7 again to run essential programs but there is no record of it.

I do not have a cd drive so this is further complicated by trying to load windows 7 from a usb. I already have the working usb--I tested in on other computers already and it works fine.

Seems I need to create a windows Master Boot Record for windows again. But I am having the hardest time finding the guide online to do this. There are hundreds of guides to help you set up Linux within Windows but there seems to be almost nothing for people who need to go back to windows but lack a cd drive.

I assume this is not the first request for this, but I have searched for 3 days in vain. If anyone out there can put a link to this solution in front of my face, I would be so grateful.

Best regards,

Peglegtrading

---

### Post by oldfred on 2010-08-18
Having windows in the MBR will not let you boot windows unless you have reinstalled windows. And reinstalling windows will overwrite the MBR with the windows boot loader. 

To install windows you have to boot the USB which if set up properly should boot windows install or recovery.

Create Windows 7 USB 
[http://technet.microsoft.com/en-us/magazine/dd535816.aspx](http://technet.microsoft.com/en-us/magazine/dd535816.aspx)

---

### Post by kbless7 on 2010-08-18
If you completely wiped your hard drive when you installed Ubuntu, you won't be able to recover Windows at all. 

If by chance you didn't do that and put Ubuntu on a different partition, then you can boot from the Windows USB and run the repair option. This will reinstall the Windows MBR.

---

### Post by peglegtrading on 2010-08-18
Hi there,
 
Thanks for your feedback. 
 
Well I have assumed that windows has been completely wiped away and I did some further damage to the ubuntu installation.
 
When I try to boot up using the usb with properly formatted windows xp iso I get the following error:
 
/ubnkern initrd=/ubninit
 
I assume this is referring to the ubuntu kernel. 
 
I guess I need to take care of this problem before I can get anything else running on my pc.

---

### Post by peglegtrading on 2010-08-18
Ok a little progress. I finally got supergrub to boot on my pc. But when I try to create the win mbr I get the following message:
 
set aux_hd"hd80"
dd (fd0)/boot/sgd/brs/syslinux.bin (hd0) 0 0 300
 
I assume this means the windows sector is unrecoverable? Really no clue...

---

### Post by enenalan on 2010-08-18
Yeah dude....if you wiped your partition of any semblance of Windows 7, I'm not sure how you could get it back.  I mean, that's basically what that option in the install does.  Short of using some kind of recovery software for whatever files you were looking for, I'm not sure how you'd muster it......  Even then, Linux might have already written over them.  I think a reinstall would be you only way of getting Windows 7 back.....minus your files.....

---

### Post by peglegtrading on 2010-08-18
yeah need to do a new install for sure. Ok so I reformatted the hd to ntfs--it seems I had already deleted the linux hdd (I am not sure what the call the linux configuration for a hdd). Now that the HDD is in ntfs I hope this will allow me to reinstall windows from the usb. If not I have just deleted two os' and accomplished nothing. Hope this is the end of my trials.

---

### Post by C.S.Cameron on 2010-08-18
If you need to make a Windows 7 install USB, you need to format the USB as NTFS, set the boot flag and copy the contents of the windows install disk to it, (or extract a Win7 iso to it).

---

