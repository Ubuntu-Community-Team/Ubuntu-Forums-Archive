---
title: "HELP - FSCK maunually - GRUB Error 15 !!"
date: 2006-03-12
forum: General Help
---

### Post by MJSOnline on 2006-03-12
Hi all. I got a big problem here.  
I booted my desktop system up as normal, spotted the updates icon on the taskbar at the top of the screen, I went to click it to see if I can install/view them and got the error message **"Permission denied.  Read / write error.  Permissions"**.

What went wrong?

I then rebooted the system, just thinking it was a bootup problem and recived the following error...

**"Cannot run fsck - run mannully using "mount -n -o mount,rw /"**

What did that mean?  I ran it as it said and got this.. 
**"bad magic number in super-block while trying to reopen"**  A

Then after saying yes to fix it - rebooted and got the **"Grub error 15"**  Also the date and time on the files it listed where all "Sun Aug 12 23:15:37 2005"

Now my system wont bootup at all.  What when wrong?  How do i fix it?  Have I losted all the data on my 2nd harddrive?  Thanks.  Matthew

---

### Post by MJSOnline on 2006-03-12
Anyone got any ideas?  Thanks. Matthew

---

### Post by kaamos on 2006-03-12
I have no idea what could cause that, but you could hopefully use a live cd to save your data. So try booting with a live and mounting that hd.

---

### Post by powder on 2006-03-12
I found this in the Gentoo documentation regarding GRUB Error 15:

> This error is returned if the specified file name cannot be found, but everything else (like the disk/partition info) is OK.

Frequently, the error notes a missing kernel image file. Make sure that the file it is referring to exists on your boot partition.

To find out the exact name of your kernel, boot from the installation cd, mount your root and (if applicable) boot partition. Next, chroot into your Gentoo system and do a listing of the available files to see what kernel images you have available: 

I would boot up a live CD, mount your disk, change to /boot, and make sure the kernel image is there.

---

### Post by dcstar on 2006-03-12
[QUOTE=MJSOnline]
.....
Now my system wont bootup at all.  What when wrong?  How do i fix it?  Have I lost all the data on my 2nd harddrive?  Thanks.  Matthew[/QUOTE]

Possibly a major hardware problem with the drive, you may be able to recover the data with care.

---

