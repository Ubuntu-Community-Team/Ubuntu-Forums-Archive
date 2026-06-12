---
title: "Accidently delete files in Windows system drive from Ubuntu."
date: 2011-08-17
forum: General Help
---

### Post by ravindukelum on 2011-08-17
I have dual boot ubuntu 10.10 and Windows XP and Accidently, Some files in XP system drive files got deleted and now canot boot into Win XP,

These are the files left and nothing happend to folder....

AUTOEXEC.BAT
boot.ini
CONFIG.SYS
IO.SYS
MSDOS.SYS
ntldr

What is the missing file and how to replace it or fix boot into xp again.

---

### Post by Brad55 on 2011-08-17
What is the error message that you get when trying to boot into XP?

---

### Post by seawolf167 on 2011-08-17
You can try restoring the Windows XP partition boot record and see if that helps. Insert your Windows installation disk, boot off of it, then enter the Recovery Console. Once there, type in the following command

```
fixboot C:
```

Reboot, and see if you can boot into XP

---

### Post by HereInOz on 2011-08-17
I would guess that the file(s) you are missing are:
NTDETECT.COM
and 
if you have left the page file in the default location, 
pagefile.sys.

I think you are in trouble.  You may be able to get things back by copying the NTDETECT.COM file from another XP machine. It normally doesn't get modified in the life of the system.

I have no idea what will happen if you have deleted the page file.  Never done that before.  This is why you should never share the root or system directories of a drive - too easy to blunder into disaster.

---

### Post by WorMzy on 2011-08-17
Check to see if the files are in .Trash-1000 (press Ctrl+h to see hidden files and folders in nautilus)

---

### Post by oldfred on 2011-08-17
Part of why I usually suggest a separate shared NTFS partition for read/write and only set c: as read only.

If it is just boot files that are missing:

If files are still missing you can do this to copy from CD to C:\:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.
or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

Yoiu also need boot.ini
How to edit the Boot.ini file in Windows XP
[http://support.microsoft.com/kb/289022/](http://support.microsoft.com/kb/289022/)


meierfra. - How to fix XP when the boot files are missing
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

