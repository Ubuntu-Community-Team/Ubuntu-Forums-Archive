---
title: "hard drive shows in bios but not on Ubuntu"
date: 2011-03-18
forum: General Help
---

### Post by threee6 on 2011-03-18
i have just put in my new 320gb seagate hdd and it shows in bios, however upon booting from USB it does not show on the OS, nor does it show on the installer :( does anyone have any idea what could cause this or how to sort it? and help would be great as it trueley sucks lol thanks. threee6

---

### Post by pricetech on 2011-03-18
Check your hard drive settings in the BIOS.  You may need to set some kind of "compatibility" setting for the drive to be seen.

How exactly are you trying to see the drive in Ubuntu ??  Have you run fdisk or gparted ???

---

### Post by threee6 on 2011-03-18
we managed to get it to be viewable in disk utility and found that it was formated as a RAID device, so we formated it for ubuntu, it mounted and let us view the drive, as soon as we try and install its not showing up on the installer, i have tried the drive in another computer and have the same problem, a friend of mine has taken it to try in his PC and see if he can get it to work, i will let you no if he has any luck shortly and if he does, how he did it.. :)

---

### Post by pricetech on 2011-03-18
Meanwhile, check the manufacturer's site for a diagnostic utility.  You may have a bad drive.

---

### Post by oldfred on 2011-03-18
If it is not a RAID but was, then it saves meta data on the drive that causes problems with the liveCD. If it is two or more drives with RAID then the alternative installer works better than the liveCD.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

If you are sure you do not have RAID running:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by threee6 on 2011-03-18
thanks all :) running -

sudo dmraid -E -r /dev/sda

sorted the problem :) thank god, for a second there i thought i was gunna have to use windows lol

---

