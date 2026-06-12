---
title: "Dual Boot to Single Boot Separate HDs"
date: 2010-07-25
forum: General Help
---

### Post by silouette747 on 2010-07-25
Here's my situation:

I have two hard drives one with Windows XP and one with Ubuntu 10.04

The hard drive with Windows XP has been dying out slowly over the last week thankfully I backed up all my important information. 

The problem is that now that the Win XP hard drive is dead I can't boot into Ubuntu nothing pops up just the blinking cursor.

I believe this is because when I installed ubuntu the Windows XP HD was already in the first slot and may have all the boot information.

How can I fix this?

Note: I have the LiveCD and can boot into that successfully.

---

### Post by robsoles on 2010-07-26
That's a pain in the neck.

Please remove failed XP HDD and start machine, boot from LiveCD.

Under 'Places' (in GUI/Desktop) look at entries listed under 'Computer' entry and find your 10.04 LTS OS HDD drive, click it and it will be mounted under media using the name you see in the list under 'Places'.

Open "System"->"Administration"->"Disk Utility" and find out what the '/dev/' name of the drive is, assuming that the '/dev/' name is '/dev/sda' and that the mount point was '/media/your-hdd' (please change both appropriately for your actual names!)
```
grub-install /dev/sda --root-directory=/media/your-hdd/
``` typed into terminal should give you a bootable Ubuntu 10.04 LTS OS again - please post back your actual result... (Or request for info/better detail coz you can't follow my post)

You may need to use 'sudo' at the start of the line I am currently starting 'grub-install' - can't remember, didn't have to do it for a while!

---

### Post by silouette747 on 2010-08-14
Worked like a charm! Sorry for the late response :)

---

### Post by robsoles on 2010-08-14
> **silouette747 said:**
> Worked like a charm! Sorry for the late response :)

Glad to hear it, please consider using 'thread tools' above in red to mark this thread as solved.

---

