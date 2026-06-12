---
title: "Fix Windows XP ntfs from ubuntu"
date: 2010-07-27
forum: General Help
---

### Post by palz2015 on 2010-07-27
I used [http://ubuntuforums.org/showthread.php?t=521207](http://ubuntuforums.org/showthread.php?t=521207) for the commands. When I run:

ntfsresize --no-action --force /dev/sda1

via 9.10 live cd on an old toshiba tecra, it gives me a permission denied error.

This is because I need to recover files before I reformat.

---

### Post by typal on 2010-07-27
Are you sure you don't just need to toss a sudo in front? What exactly are you trying to do?

---

### Post by efflandt on 2010-07-27
If you are trying to resize or move a partition, that is easiest to do with **gparted** (which is on an install CD or you can install using Synaptic on a system.  However, you cannot resized a partition that is mounted, or maybe even if something on that drive is mounted.  So you may need to do that from live/install CD (or bootable USB) if trying to modify your main drive.

If gparted detects a problem with an ntfs partition, it will suggest running **chkdsk /f** on it from Windows to fix it, and will not touch it until you do.

But even if doing things correctly, it has to be done as root, and is why the **sudo** suggestion.

---

### Post by Mark Phelps on 2010-07-28
You can try running ntfsfix to repair the ntfs volume.

However (from the ntfsfix man page):  

> ntfsfix is a utility that fixes some common NTFS problems. ntfsfix is NOT a Linux version of chkdsk. It only repairs some fundamental NTFS inconsistencies, resets the NTFS journal file and schedules an NTFS consistency check for the first boot into Windows. 

So, if it does NOT fix the volume, you will have to fix it with chkdsk run from MS Windows.

---

### Post by prodigy_ on 2010-07-28
Also you can use avast! Disk Checker from their [bootable CD](http://www.avast.com/bart-cd).

---

### Post by palz2015 on 2010-07-29
OK i still can't see the contents of the volume. Just like before.

See, I ran check in gparted, and said I needed to run chkdsk. So I run sudo ntfsfix /dev/sda1 and it seems to work, but no.

And check in gparted gives the same error (second image).

In windows, I get: Insert system disk press any key to continue
over and over and over.

---

### Post by palz2015 on 2010-07-29
Weird: also I get a black screen when trying to boot an XP pro dvd: like I used to when trying to boot from the xp install on the dvd.

sorry  for my english, kinda rushed and tired.

---

### Post by prodigy_ on 2010-07-29
Just to clarify: you tried to boot from an XP installation CD and all you saw was a black screen, correct?

If so, it might be a scratched CD or a hardware issue.

---

### Post by palz2015 on 2010-07-30
It must be some kind of hardware issue. The CMOS is dead, btw.

---

### Post by palz2015 on 2010-07-30
Or this may be a drive issue. All I know is, at first, it booted to the logon. Then, I saw a flash of BSOD and reboot. Then, just a black screen (f8 didn't work, nor did the boot device selection). Now, Insert system disk in drive. Weird, eh?

---

### Post by prodigy_ on 2010-07-30
> **palz2015 said:**
> Or this may be a drive issue.
Might be a motherboard problem. Anyway, it should be easy to test your HDD if you have access to another PC.

---

### Post by palz2015 on 2010-07-30
Would that need an enclosure? Its a thin drive with one port. After the system drive messages started, I pulled out the drive and blew on the contacts. So I'm about to just format it. look at the screenie (accidentally set the language to esperanto :popcorn: :

---

### Post by palz2015 on 2010-08-02
OK something good happened: I was able to get to "We are sorry for the inconvenience but Windows did not start correctly" screen. It rebooted when I chose safe mode, and it started to boot when I pressed "Start Windows normally", but flashed a BSoD and rebooted. Now I cannot get to it anymore, and I still cannot access files on the drive, though it tells me how much free space there is.

---

### Post by palz2015 on 2010-08-02
Bump, please help

---

### Post by Mark Phelps on 2010-08-02
Until you can see the BSOD and read the stop code, you will not have any way to diagnose or repair the WinXP problem.  And, you're certainly NOT going to be able to do that by using Ubuntu or any Linux utiulities.

You need to figure out a way to get back into WinXP using SAFE mode.  Maybe pressing F8 when you reboot will eventually get you a text screen where you can choose safe mode.

Once there, and onto a desktop, see the details in the link below for how to set your machine to stop restarting on BSODs:

[http://www.friendsintech.com/index.php/archives/90]("http://www.friendsintech.com/index.php/archives/90")

---

### Post by palz2015 on 2010-08-02
Thanks, I'll look into it.

---

