---
title: "Error: Unable to mount location, Not authorized"
date: 2010-06-26
forum: General Help
---

### Post by catsails on 2010-06-26
Hey all,

As of today, I am unable to access my D: drive, when I try, I get the message "unable to mount DATA. not authorized." (data = name of drive)
I'm running ubuntu 10.04 installed through wubi. So I can load either windows or ubuntu, the DATA drive is a music/media drive without any system files in it that is shared between windows and ubuntu.

I am guessing this is a permission thing, since I have the update manager set to automatically download updates every 2 days, because I was able to access the drive a few days ago. However, I don't know what's causing the issue, and I'm too much a noob to know how to resolve it once I figure out specifically where the problem is. 
Little help?

---

### Post by dabl on 2010-06-26
I'm not a WUBI user and not a NTFS user, so ....

Alt-F2 and
```
gksudo nautilus
```

browse to "DATA".  Are the data files right on the drive itself, or in neatly-organized folders like "MUSIC", "IMAGES", "VIDEOS", etc.?  Ideally it's all in folders, and you can do the following for each folder:  Right-click "properties", and click the "Permission" tab.  In the two windows where it says "root", change that to "catsails" (or whatever your user's name is), and check the box that says "Apply to subdirectories and files".

In Linux, the recommended arrangement is to let root be the owner of "devices", such as the hard drive/partition, and then let the user(s) be the owner of folder/directories on the device.  So root should own D:, and catsails can own folders on D:.  But, you can always throw caution to the wind and make you user the owner of the drive if you want to.

---

### Post by catsails on 2010-06-26
Unfortunately, I can't browse to Data with nautilus. Nautilus seems unable to go any directories higher than the File System, when I try to go to Computer to get to DATA, I get the error "Could not display "computer:". Nautilus cannot handle "computer" locations."

If I just use the normal file browser and check the properties of DATA, it says the permissions could not be determined.

---

### Post by catsails on 2010-06-26
So, I have now rebooted in windows, and whatever has happened to ubuntu has also had the effect that I can not restart or shutdown. Either option simply takes me to the login screen, so I had to manually shut off the computer to reboot.

---

### Post by dabl on 2010-06-26
Which version of Windows is it?  It sounds like maybe some change in either the BIOS or the bootloader affected the designation of drives and partitions, or something like that?

---

### Post by catsails on 2010-06-26
It is Vista. Windows is still running fine, happily. So I think the problem is ubuntu specific. I imagine a complication arising from doing the wubi install rather than formatting the drives properly.

---

### Post by catsails on 2010-06-30
It has become much more exciting! Now, ubuntu will not load at all. When I select ubuntu from the boot menu, I get only Grub. Apparently, wubi has problems when you force shut down. I could accept this, if it didn't force me to force shut down by just returning to the log in screen whenever I tried to shut down normally. So now, unless anyone has a magic solution, ubuntu is gone. Indeed, even if I just check the ubuntu folder in windows, it seems very much empty, so I don't know what happened.

I think my plan will just be to wipe the drive and install ubuntu properly this weekend, as I'm fairly sure the problems I've been having are Wubi-specific ones. Wubi was at least useful in that it gave me a taste for ubuntu.

---

