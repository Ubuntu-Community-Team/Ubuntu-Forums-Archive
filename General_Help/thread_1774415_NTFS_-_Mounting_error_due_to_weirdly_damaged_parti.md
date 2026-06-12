---
title: "NTFS - Mounting error due to weirdly damaged partitions."
date: 2011-06-03
forum: General Help
---

### Post by chooyanzou on 2011-06-03
I have this freakishly weird problem.

I have an "old" disk from a laptop. The disk is devided into three NTFS-partitions:

1) WinRe
2) Vista
3) Data

The laptop stopped beeing bootable the other day and when I tried to mount it using Ubuntu LiveCD I got these really weird problems...
[INDENT]***fdisk -l***
[/INDENT][I]sda1   ntfs     WinRe   15GB
sda2   ntfs *  Vista     60GB
sda3   ntfs     Data     60GB[/I]

The weird thing is that only sda1 and sda3 is mounted and everytime I try to mount sda2 I get errors refering to MFTMirr and the mounting fails.

When I run ntfsfix on sda2 I get the message that the disk is OK, but when I run ntfsfix on sda3 I recieve a message that tells me that sda3 is damaged and can't be repaired.

The exit error code when trying to mount sda2 is 18.

Is there anyway I can rescue this partition using Ubuntu LiveCD? Restore the filesystem, bootsector or anything? I have been looking at the possibility of using ntfsclone but my Linux skills can only take me so far.

You help is appreciated.

/C

---

### Post by oldfred on 2011-06-03
Ubuntu/gparted/Linux will often not mount a NTFS partition that needs chkdsk to prevent additional damage that then chkdsk would not be able to repair. I would run chkdsk on all the NTFS partitions and rerun until there are no errors as it does not always fix everything on one pass.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Repair Disc at the following links:
Windows Vista Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Windows 7 Disc - for repairs only
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not auto repair XP (they create the boot sectors differently) but can run chkdsk on any NTFS partition.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by chooyanzou on 2011-06-07
Thanks **oldfred**!

I will try it first thing when I get home from the university. Funny problem to have when studying computer science, whouldn't you say?  =)

I'l get back to this thread with the result and mark it solved if I manage to rescue the disk.  :)

---

### Post by chooyanzou on 2011-07-09
It was a struggle to the bitter end. I had to use a Vista Recovery disc to run **chkdsk** about a million times. After this battle it still didn't want to boot. I turned out **chkdsk** didn't manage to repair the filesystem enough for Vista to boot, but enough for **Ubuntu Live-CD** to boot and rescue the whole disc content. Didn't even have to use any file recovery tools, the files were intact. Windows is such a crybaby...

Thanks for your help **oldfred**.

---

