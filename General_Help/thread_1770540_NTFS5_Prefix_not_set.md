---
title: "NTFS5 Prefix not set"
date: 2011-05-29
forum: General Help
---

### Post by Ishana on 2011-05-29
Ubuntu was working perfect for 3 months or more , but now all of a sudden after I restarted because I had massive lag, I found that I can no longer open Ubuntu.
The error I get is "NTFS5 Prefix not set".
Now I get black terminal when I open ubuntu..

Also, I do not have any other OS installed and I can't install them

---

### Post by oldfred on 2011-05-29
Are you mounting a NTFS partition as part of your install? Have you run chkdsk on it lately? Ubuntu runs fsck on its partition every 40 boots or so.

---

### Post by Ishana on 2011-05-29
> **oldfred said:**
> Are you mounting a NTFS partition as part of your install? Have you run chkdsk on it lately? Ubuntu runs fsck on its partition every 40 boots or so.

Yes, and chkdsk is a Ubuntu terminal command?

I am all new to this, and sadly almost no knowledge at all :(

---

### Post by oldfred on 2011-05-29
No chkdsk is windows command line. Yes windows does command lines. But usually windows just runs it on reboot, so you never see it.

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

### Post by Payero on 2011-09-22
For what is worth, I was having the same issues after having Ubuntu 11.0.4 up and running for over a month.  After looking at the files system under Windows I noticed that my root.disk file had 0 bytes.  Something, either Windows 7 or Ubuntu itself, corrupted the file.  Luckily I had a backup of my computer including my ubuntu install so I was able to recover by replacing the bad root.disk file with a previous version.  Hopefully this information would throw some light into this problem.

---

