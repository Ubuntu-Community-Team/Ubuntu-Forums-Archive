---
title: "Uninstalling Ubuntu"
date: 2012-03-14
forum: General Help
---

### Post by Coltorl on 2012-03-14
**(Resolved)**
I recently built a computer. 
My Specs: FX-4100 CPU
Radeon 6870
500 GB 7200 RPM HDD (Ubuntu is on here)
8 Gigs of Ram


And since I didn't have a copy of Windows at the time I thought it would be a cool idea to put Ubuntu on here. I got a windows 8 disk but It does not want to autorun from the bios screen. I have set the cd/rom as the primary booter. Is there a way to wipe my HDD clean of ubuntu? And I don't want to dual boot it. I just want to wipe it clean. Thanks.

edit: If I burn Windows 8 onto a cd do you think it will autorun and install it?

---

### Post by wyliecoyoteuk on 2012-03-14
If you can't boot the windows CD, removing Ubuntu won't make it boot, as the boot setup is a BIOS thing, it happens before the OS is loaded.

---

### Post by Coltorl on 2012-03-14
Well how Do I uninstall ubuntu? I know it is automatically booting up with the HDD even when I tell it not to.

Edit: What software can I add to ubuntu so that it can read an iso like windows 8 and install it?

---

### Post by QIII on 2012-03-14
Ubuntu isn't going to let you pop in the Windows CD over itself any more than Windows would do it the other way around.

Start your machine with the Ubuntu CD in the drive and enter a live session.  Go to the terminal and type

```
gksudo gparted
```

That will bring up a nice GUI partitioning tool.

Delete the current partition(s) on your hard drive and create one large NTFS partition.

Log out of the Live session, shut down and remove the LiveCD when prompted.

You will be left with a nice, clean, blank disk waiting for Windows to be installed.

If you can't install from there, you need to check your BIOS again.

---

### Post by Coltorl on 2012-03-14
Ok I'll try that.

---

### Post by Coltorl on 2012-03-14
It now says in the BIOs screen

Unknown File System
Grub_Rescue

---

### Post by QIII on 2012-03-14
That would seem to indicate that your Master Boot Record (MBR) from the Ubuntu install is being reached.  If you are booting from CD/DVD that should not be happening.  The Windows installation should be starting and overwriting that.

Are you 100% sure your optical drive is first in the boot order and that the drive works?  Is your Windows disk a licensed, uncopied one?

If you start with the Ubuntu CD in the drive, do you go to an Ubuntu live session?

---

### Post by Coltorl on 2012-03-14
I got a copy from the internet. But if I know it will work I will go ahead and buy an OS. Thanks for your help :).

---

### Post by QIII on 2012-03-14
Since you pirated the OS, my help ends here.

This is not a place where requests for help in nefarious or illegal activities are tolerated and I do NOT appreciate the insult to my character.

---

### Post by Coltorl on 2012-03-14
No, I got the Windows 8 Consumer Preview not a pirated Windows 7.

---

### Post by Mark Phelps on 2012-03-15
Win8 CP will not fit on a CD; it requires a DVD.  But, once you have the ISO burned to that, it WILL boot and install.

If the optical disk is not booting, then either it wasn't created right, or your boot order is not set right.

If you REALLY want help installing Win8, then go to the proper forum: eightforums.com.  They have threads and tutorials dealing with installations.

---

