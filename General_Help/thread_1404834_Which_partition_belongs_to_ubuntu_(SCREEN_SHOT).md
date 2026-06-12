---
title: "Which partition belongs to ubuntu? (SCREEN SHOT)"
date: 2010-02-11
forum: General Help
---

### Post by howdoyou on 2010-02-11
I had ubuntu installed, then i uninstalled it useing the CD in windows, here is a partition list, is ubuntu gone? is the partition still taken up? i'm a bit confused...

[http://yourfilespot.com/users/204421932.png](http://yourfilespot.com/users/204421932.png)
[IMG]http://yourfilespot.com/users/204421932.png[/IMG]

---

### Post by Deadseraph on 2010-02-11
Windows is the only OS that runs an NTFS filesystem as far as I'm aware, and none of those are a root filesystem or /boot, so I'd say yea, it's gone.

---

### Post by abhishek.malhotra35 on 2010-02-11
None of the partition looks like of ubuntu. Do you have a secondary harddisk on which ubuntu is installed.

---

### Post by jblaven on 2010-02-11
Did you manually reformat any of the partitions after using the CD?  I would have expected the partition to still be there.

---

### Post by synapsys on 2010-02-11
hoo-ray for backtrack!

---

### Post by 2hot6ft2 on 2010-02-11
> **howdoyou said:**
> I had ubuntu installed, then i uninstalled it useing the CD in windows
51GB is a lot of used space in windows and since you say you used it IN Windows did you install it INSIDE Windows?
A WUBI Install? Or did it ever have it's own partition?

---

### Post by howdoyou on 2010-02-11
i downloaded the iso, burned onto cd, put the cd back into the computer whall i was running windows7, i installed it in windows7, restarted the computer, and then i had the option to run windows7, or ubuntu. after updating today it didnt work anymore, keep restarting the computer, so i uninstalled it by booting into windows7, putting in the cd, and uninstalling it. does that mean it was never partitioned in the first place?

---

### Post by darolu on 2010-02-11
No, you made a Wubi install, what it does, is it creates a Virtual Machine inside Windows and then rewrites your MBR to give you direct access to it; Ubuntu was installed IN Windows, kinda like all your other apps, when you formatted, you deleted all programs in the process, including Ubuntu (Wubi).

To install Ubuntu (hard way) you need to boot from the Live CD and install with it, you will then re-partition your hard drive.

Look at this link for more information: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

In case you're having problems booting from the CD: [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by l-x-l on 2010-02-12
> **howdoyou said:**
> after updating today it didnt work anymore 

What exactly did you update? Windows or Ubuntu? Also what didn't work anymore? (I'm assuming Ubuntu)

> **howdoyou said:**
>  keep restarting the computer, so i uninstalled it by booting into windows7, putting in the cd, and uninstalling it.

You didn't need to put in the CD to uninstall it. Simply uninstall it like you do any other windows program.

---

### Post by bronquel on 2010-02-12
we gather you did a wubi install... but after that it's a little fuzzy.  if you check in windows under your add remove programs, can you still see ubuntu?

---

### Post by howdoyou on 2010-02-12
no, its gone now.

what happed is when i logged into Ubuntu, it said i had updates to install, so i installed them, after installing it asked for a reboot, so i said yes to the popup box - which rebooted the computer. when the boot menu came up i selected Ubuntu like i always do - and it would just restart the computer and go back to the boot menu again. I figured there was a bad update or something, windows still worked fine etc, but Ubuntu would not boot. so i uninstalled it.

---

