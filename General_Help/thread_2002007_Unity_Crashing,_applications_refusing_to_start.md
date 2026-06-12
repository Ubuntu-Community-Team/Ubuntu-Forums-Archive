---
title: "Unity Crashing, applications refusing to start"
date: 2012-06-12
forum: General Help
---

### Post by Woegjiub on 2012-06-12
This is really quite bad.

After about an hour or so, applications start to freeze up, unity seizes up, and things refuse to launch.

Compiz has just crashed, and the only things I can do in the GUI are left-click and type in firefox, and use the nautilus desktop background menu.

I can not even alt-tab, open up any other programs, click on them to raise them, or restart unity/compiz.
Even the right-click menu in firefox is not working.


I thought it may be an issue with a hard drive, but disk-utility shows no errors with the drive containing my operating system.

Could someone please help? This is not fun at all.

---

### Post by stinkeye on 2012-06-12
Log into the Ubuntu 2d session and use that for a while and
see if the same occurs.

---

### Post by Woegjiub on 2012-06-12
After resetting (with the physical button), the computer becomes stuck on the ASUS screen, and will not progress until it has been turned off and then back on manually.

Things are saying that the system drive is read-only, despite this not being the case.

---

### Post by Woegjiub on 2012-06-12
Well, it still happens in Unity 2D.

If I attempt to create a folder on my desktop, this is the error message it brings:

"Error while creating directory Untitled Folder.

There was an error creating the directory in /home/darko/.Desktop.

Error creating directory: Read-only file system"

Does anyone know what could cause my root partition to become read-only?
I am presuming it is either a physical problem, or something in the kernel :/

---

### Post by Woegjiub on 2012-06-12
It appears as though / is being completely unmounted, as attempting to login at TTY1 throws an I/O error, then goes back to the login prompt.
The filesystem is unbrowsable also.

After a reset with the button, the BIOS is stalling at loading one of the hard drives, but this is remedied temporarily by a complete power-off as described above.

---

### Post by wilee-nilee on 2012-06-12
Sounds like bad install or tweaked to far, or drivers missing or incorrect.

Maybe bad hardware as another possibility. 

Have you done a memory check lately from the option on the live cd lately, or a smart disc check?

Is this a true dualboot or a wubi or a virtual install?

---

### Post by Woegjiub on 2012-06-12
> **wilee-nilee said:**
> Sounds like bad install or tweaked to far, or drivers missing or incorrect.

Maybe bad hardware as another possibility. 

Have you done a memory check lately from the option on the live cd lately, or a smart disc check?

Is this a true dualboot or a wubi or a virtual install?
This is a true dualboot, although ubuntu is my primary OS, and windows is completely unused except for a Diablo 3 installation.

I have removed the metapackage for the ubuntu install, because it refused to associate .png files with gwenview instead of EoG, so that scrolling would browse images, but apart from that, everything is close enough to vanilla.

Compiz etc are all unchanged, my fstab is the same as normal for the root drive, etc...

I am now running from the livedisc, so that I can see if it still occurs.

---

### Post by sahabcse on 2012-06-12
Any error information in /var/log/messages?

---

### Post by wilee-nilee on 2012-06-12
> **Woegjiub said:**
> This is a true dualboot, although ubuntu is my primary OS, and windows is completely unused except for a Diablo 3 installation.

**I have removed the metapackage for the ubuntu install,** because it refused to associate .png files with gwenview instead of EoG, so that scrolling would browse images, but apart from that, everything is close enough to vanilla.

Compiz etc are all unchanged, my fstab is the same as normal for the root drive, etc...

I am now running from the livedisc, so that I can see if it still occurs.

How did you remove this ubuntu meta package, to be honest that may be the root of your problem.

The Ubuntu desktop is unity, so this is a little confusing.

---

### Post by Woegjiub on 2012-06-12
> **wilee-nilee said:**
> How did you remove this ubuntu meta package, to be honest that may be the root of your problem.

The Ubuntu desktop is unity, so this is a little confusing.
In the software centre.
It is only the metapackage, the others were unaffected.
It refused to remove eye of gnome without doing that.

The problem appears to be that my 128GB SSD (Crucial M4) has carked it.

Lovely, right? Those things are annoyingly expensive, and it was less than 6 months old.

---

### Post by Woegjiub on 2012-06-12
> **sahabcse said:**
> Any error information in /var/log/messages?
The system drive is unmountable from the live disk, giving a "bad superblock" error.
The windows partitions are also inaccessible, so I am presuming the entire drive is dead.

dmesg shows a massive trail of SDA read errors on a large number of sectors.

[http://www.tomshardware.com/news/Crucial-m4-Firmware-BSOD,14544.html](http://www.tomshardware.com/news/Crucial-m4-Firmware-BSOD,14544.html)
"Crucial  stated that the firmware "Corrects a condition where an incorrect  response to a SMART counter will cause the m4 drive to become  unresponsive after 5184 hours of Power-on time. The drive will recover  after a power cycle, however, this failure will repeat once per hour  after reaching this point. The condition will allow the end user to  successfully update firmware, and poses no risk to user or system data  stored on the drive". "

---

