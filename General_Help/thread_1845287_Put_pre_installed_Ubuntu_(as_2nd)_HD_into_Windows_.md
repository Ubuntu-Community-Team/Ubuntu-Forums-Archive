---
title: "Put pre installed Ubuntu (as 2nd) HD into Windows PC?"
date: 2011-09-16
forum: General Help
---

### Post by candtalan on 2011-09-16
I would appreciate comments about putting an Ubuntu (10.04.3, updated) hard drive, as a second hard drive, into a Windows PC which already has a single hard drive.
What first comes to mind is how to boot initially  to get grub  working usefully.

Do I use the procedure with a live CD to reinstall grub onto the Ubuntu partition and then update-grub?
(which writes to the MBR?)

Should I anticipate significant problems with video or other drivers because the Ubuntu was installed in an alien PC first? 

I am hoping to use this approach  for a PC of a friend who I am briefly visiting soon, and hoping to avoid a longer, normal, installation process.

tia

---

### Post by ajgreeny on 2011-09-16
Try putting the drive in and then, in the BIOS choose it as the first boot device.  You may find that Ubuntu runs perfectly, and the command ```
sudo update-grub
``` in terminal will add windows to the grub menu.

If that is not successful, try the other drive as first device, as adding drives can confuse systems sometimes.

If neither works, use the boot-info-script in my signature to download and run the script from a live CD or USB, then post the RESULTS.txt file back here in code tags, the # icon in top toolbar of the reply box.

---

### Post by varunendra on 2011-09-16
I don't think that much work will be required. Just like one uses the Grub boot menu to select the OS to boot, one can also choose to bring up the BIOS boot menu (most often by pressing F9/F12/F10/F8 or Esc) and choose the 'Hard Disk' to boot :)

Although the "update-grub" thing is supposed to be the standard way, I prefer choosing the disk from BIOS menu as it seems to me a bit quicker.

@candtalan,
As for the video or other drivers issue, it depends upon what kind of card the destination PC has. Most often, it is picked up and configured automatically, but sometimes you may need to boot into safe graphics mode then install proprietary graphics drivers for the card. But in that case, you'll end up doing the same even with the fresh install anyway, so go ahead.

---

### Post by wildmanne39 on 2011-09-16
Hi, I recently installed ubunutu on a disk drive from another computer using my computer and all I had to do was update grub from ubuntu and install the video card driver.

The way ajgreeny suggested should work well.
Thank you

---

### Post by dcstar on 2011-09-17
> **candtalan said:**
> 
..........
Should I anticipate significant problems with video or other drivers because the Ubuntu was installed in an alien PC first? 


If you **haven't** installed propriety video drivers on the original install then you should be ok as the boot-up process will auto-detect the different hardware.

The UUIDs of the hard drive partitions in /etc/fstab now bypass the old issue of /dev/hdx designations changing when doing this sort of thing.

---

