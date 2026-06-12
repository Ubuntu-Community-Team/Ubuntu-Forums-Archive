---
title: "Suspected failing harddisk"
date: 2011-01-18
forum: General Help
---

### Post by jongudm on 2011-01-18
I need some advice on how to diagnose a possibly failing harddisk.  This is the system disk of a Windows XP machine that will not boot.  It gets to the "progress bar" that runs across the screen a few times but then it always stops in the same spot.

If I boot from a live Ubuntu CD what tools should I use to find out if the disk itself is failing?

The disk is under warranty but if I take it to the shop and the problem turns out to be software errors then I have to pay so I want to be sure what is going on before going there.

Any advice would be much appreciated.

---

### Post by coffeecat on 2011-01-18
> **jongudm said:**
> If I boot from a live Ubuntu CD what tools should I use to find out if the disk itself is failing?

From a live CD session, System > Administration > Disk Utility. Select the drive and look for SMART status. Below that you can view SMART data and run self-tests.

---

### Post by coffeecat on 2011-01-18
EDIT: duplicate post because of forum issues.

---

### Post by jongudm on 2011-01-18
When I run the Disk Utility it says SMART status: Not supported.  I tried running the filesystem check which came back saying the filesystem is clean.

I bought this drive two years ago, it is a Western Digital 500GB SATA drive.  Shouldn't it support SMART?

---

### Post by srs5694 on 2011-01-18
Try installing the gsmartcontrol package under Ubuntu (you should be able to do this from a live CD), then run it, just in case Disk Utility is misreporting the SMART status of the drive.

You could try using the text-mode badblocks utility to scan for bad sectors the old-fashioned way. This might take a while and it might miss sectors that are just starting to go bad, but it's better than nothing.

The sort of problem you describe can also be caused by software issues, such as damaged driver files, messed up configurations, or even viruses. If you can't find a hardware problem, you might consider doing a virus scan and (if that turns up nothing) re-installing XP on the computer.

---

### Post by jongudm on 2011-01-19
I will try the utilities you mention the moment I get home from work, I'm fairly sure I should be able to figure them out. :oops:

Do you know if I can reinstall XP from the CD in such a way that it just repairs the present installation and leaves the data on the disk intact (installed programs and such) rather than wiping the whole drive first?  Everything on the disk is backed up but I would love not having to set everything up again...

---

### Post by coffeecat on 2011-01-19
> **jongudm said:**
> Do you know if I can reinstall XP from the CD in such a way that it just repairs the present installation and leaves the data on the disk intact (installed programs and such) rather than wiping the whole drive first?  Everything on the disk is backed up but I would love not having to set everything up again...

If you have a Microsoft XP installation disc rather than an OEM manufacturer's restore disc (which is a different thing), you can select the repair console rather than the install option. This leads to a simple command prompt. More here:

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

A chkdsk and fixboot would be first on my list. However, if it is a virus that's causing the problem that will not help.

---

### Post by jongudm on 2011-01-19
Running chkdsk at the moment, this is taking a long time.  Apparently it found something to fix ;) ...  Then I will run fixboot and report back on the situation.

It doesn't seem to be virus related, and I would frankly be surprised if a virus got in.  But surprises happen...

---

### Post by jongudm on 2011-01-19
Chkdsk and fixboot did the trick, now the machine boots without problems!

Thanks everybody for the help :D

---

### Post by jongudm on 2011-01-20
I booted it again this morning without any problems, seems this is solved.  Again, thanks to everyone who commented on or looked at this problem.

---

