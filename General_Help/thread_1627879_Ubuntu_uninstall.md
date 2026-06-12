---
title: "Ubuntu uninstall"
date: 2010-11-21
forum: General Help
---

### Post by vipultalari on 2010-11-21
Guys I have a problem with my ubuntu. I installed ubuntu on my laptop by choosing the option completely erase my disk and install. So I don't have windows but just a fresh copy of ubuntu. I want to get my windows back and tried to boot it with a CD but my windows says no partition found. So is there a way I can install my windows again by deleting ubuntu. Please help me?

Regards,
Vipul

---

### Post by papibe on 2010-11-21
Last time I installed XP, it did not recognized anything (I'm not sure about Vista or Windows 7). Try to look for an option to "Use the whole disk", or "Format C:". You'll loose everything sadly.

If that doesn't work, you can use the Ubuntu Installation CD as a Live CD (try Ubuntu option). There you can use gparted to erase all partitions so you can make the drive more suitable for a windows install.

Good Luck!

---

### Post by garvinrick4 on 2010-11-22
If you have your original install cd for xp you are Ok.
Go into Ubuntu and open a terminal Applications/Accessories/terminal
in that terminal copy and paste this:
```
sudo apt-get install gparted
```After installed go to System/Admin/gparted
when gparted opens:
right click on Ubuntu partition or the whole drive and right click
and choose format to NTFS and hit green apply arrow and now will
be in a Windows format; You can now use your XP  installation CD to install Windows.
Next time you want to install Ubuntu choose to install side by side or manually and will not overwrite
Windows just add Linux to your partition table. It did what you told it to do, erase and use whole drive.

---

