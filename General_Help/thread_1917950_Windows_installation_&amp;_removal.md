---
title: "Windows installation &amp; removal"
date: 2012-01-31
forum: General Help
---

### Post by sunfromhere on 2012-01-31
So, I spent last month partitioning my hard drive, installing 6 Linux distros, customizing them, creating shared folders, etc, only to find out now that this laptop has a certain flaw which can be fixed by flashing BIOS which can be done only trough Windows 7.:mad: There are threads that explain Windows installation after Linux, however I have 2 additional questions:

1. Can I install Windows on an external hard? (I just need them to flash the BIOS, after that it's a removal)
2. How do I de-install Windows?

EDIT: If I were to install Windows on internal HDD, them messing up my grub, when I removed them, what would I boot into?

---

### Post by Mark Phelps on 2012-01-31
> **sunfromhere said:**
> 
1. Can I install Windows on an external hard? 
NO -- MS does not want folks using Portable versions of Windows.
> 2. How do I de-install Windows?
Boot into Ubuntu desktop CD, open Disk Utility, remove the partition you created for Win7.
But then, have to reinstall GRUB because Windows overwrote your MBR and removed GRUB from it.
> EDIT: If I were to install Windows on internal HDD, them messing up my grub, when I removed them, what would I boot into?
When you install Windows, GRUB won't work anymore -- so you will boot directly into Windows.  When you then remove the Win7 partition, your PC won't boot anymore.  You will have to reinstall GRUB from an Ubuntu desktop CD -- or, you may be able to fix it with Boot-Repair, if you create the CD for doing that:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by Cheesemill on 2012-01-31
Are you sure it has to be done through Windows 7?

If it can be done through DOS then you can easily make a bootable USB stick that will get the job done.

All BIOS's that I have ever come across allow flashing from DOS.

Let me know what make and model your laptop is and I'll take a look.

---

### Post by sunfromhere on 2012-01-31
I called HP tech support today, they told me that even though this model ships with FreeDOS, BIOS update can be only done from Windows. (His words: we ship them with FreeDOS only so that the unit doesn't come without an OS. Even if you had FreeDOS still installed, you'd still need Windows for BIOS upgrade).

When I asked him why is that, he went mute for 30 seconds, and then said in the saddest of the voices I've ever heard from tech support: "Miss, I really have no idea what to answer on that one."

:D

Then I asked him why the BIOS switch wasn't implemented in the first place, and the whole mute-sad voice-don't know scenario happened again.

---

### Post by Cheesemill on 2012-01-31
That's just stupid.

Using a FreeDOS USB stick was my plan.

Google for 'Windows PE', these are versions of Windows that can be run from a CD/USB.

---

### Post by sunfromhere on 2012-02-03
Can Windows be installed on an extended partitions? All my primary ones are taken by various Linux distros. Google gives me vague answers, mostly tending to "no".

---

### Post by dragonfly41 on 2012-02-03
Just an idea / question .. can BIOS be flashed from Wine in Ubuntu?

[http://allurgroceries.com/dellbios.html](http://allurgroceries.com/dellbios.html)

[http://java2go.blogspot.com/2010/05/how-to-upgrade-your-dells-bios-directly.html](http://java2go.blogspot.com/2010/05/how-to-upgrade-your-dells-bios-directly.html)

---

