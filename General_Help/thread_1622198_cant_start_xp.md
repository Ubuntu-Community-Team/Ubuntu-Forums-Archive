---
title: "cant start xp"
date: 2010-11-15
forum: General Help
---

### Post by slochin on 2010-11-15
hello
 Just downloaded ubuntu onto my usb thumb drive.I can open the ubuntu trial but after closing down I cannot start windows XP like I did before.If I leave the thumb drive out It starts up and then stops at 
'verifying DMI pool data A disk read error occurred press ctrl and alternate and delete to restart'.I do this but nothing happens and I am unable to get my windows xp started. If I leave the thumb drive in it automatically opens ubuntu.
Could use some help please.

---

### Post by DasEi on 2010-11-15
Wrong forum here, but way to go is use win-cd . go to recoveryconsole and run fixmbr, on irc (##windows) can get more help

---

### Post by sunewbie on 2010-11-15
Hi,

XP installation is not deleted, it is just that windows boot.ini file may be changed / corrupted. GRUB2 is the boot loader for ubuntu.

Alternatively, in case of emergency, try to Boot XP from a bootable CD.

Or, temporarily, just change the boot order in bios  from USB to Hard Disk, till you find a proper solution.  

I am not technical. Maybe some experts give you a better solution. I am also interested in the sollution as i was about to advice my friend to try ubuntu.

---

### Post by gilnic on 2010-11-15
Thank you both for response.I have my windows XP home edition disc,can't see  recoveryconsole. DasEi I am not very technical unfortunately, where do I find the recovery console?
Thank you sunewbie .Do you mean when you say try to Boot XP from a bootable CD that I should run  the setup.exe.file?
Unfortunately I do not know how to change the boot order in bios  from USB to Hard Disk when using Ubuntu.
Any further help would be greatly appreciated.
Gil

---

### Post by Kai69 on 2010-11-16
> **gilnic said:**
> Thank you both for response.I have my windows XP home edition disc,can't see  recoveryconsole. DasEi I am not very technical unfortunately, where do I find the recovery console?
Thank you sunewbie .Do you mean when you say try to Boot XP from a bootable CD that I should run  the setup.exe.file?
Unfortunately I do not know how to change the boot order in bios  from USB to Hard Disk when using Ubuntu.
Any further help would be greatly appreciated.
Gil


When you press the power button on your PC the 1st screen you see is the Bios screen on there should be an F+number to enter setup 
Note the F+number ( mine is F2 ) Reboot the PC and quickly keep tapping the F+number that should get you into Bios setup 

In Bios use the arrow keys to go to Boot menu and make sure in the list the 1st is your HDD  the information on how to change settings will be on the screen once the HDD is set to boot 1st then save and exit ...

---

### Post by warfacegod on 2010-11-16
> **DasEi said:**
> Wrong forum here, but way to go is use win-cd . go to recoveryconsole and run fixmbr, on irc (##windows) can get more help

How is this the wrong forum?

---

