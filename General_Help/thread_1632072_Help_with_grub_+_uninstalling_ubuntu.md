---
title: "Help with grub + uninstalling ubuntu"
date: 2010-11-27
forum: General Help
---

### Post by TheRevTastic on 2010-11-27
Okay I have been trying this for months now, I can't find a good way to get rid of grub and ubuntu. 

Every time I delete the partition it deletes them both but when i try to start up my computer and grub tries to load it wont as it is deleted. Then I can't even boot into windows and I don't even know how to get the Windows boot loader back.

The main reason I am doing this is because ubuntu and grub are on a 50GB partition and I need that space for windows :p. 

Anyone have any suggestions on how to do this the right way?

Thanks,
TheRevTastic

---

### Post by sikander3786 on 2010-11-27
Restore Windows bootloader from Winodws install/recovery disc. Which version of Windows is there?

Deleting the whole partition is enough to un-install Ubuntu :-)

---

### Post by TheRevTastic on 2010-11-27
> **sikander3786 said:**
> Restore Windows bootloader from Winodws install/recovery disc. Which version of Windows is there?

Deleting the whole partition is enough to un-install Ubuntu :-)

My laptop didn't come with a install/recovery disc, it came with a partition to set the windows partition back to factory default. 

I am using windows 7.

---

### Post by sikander3786 on 2010-11-27
Google "Windows 7 repair disc" and you'll find that. Burn it to disk and perform startup repair 3 times. Yes thats right, 3 times.

---

### Post by oldfred on 2010-11-27
Some links for repair disks:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

The run repairs 3 times supposedly works, but even in windows command line works better.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
BootRec.exe /fixmbr

---

### Post by asmoore82 on 2010-11-27
:lolflag: [How to Remove Linux and Install Windows]("http://support.microsoft.com/kb/314458/EN-US/")

---

### Post by TheRevTastic on 2010-11-27
> **sikander3786 said:**
> Google "Windows 7 repair disc" and you'll find that. Burn it to disk and perform startup repair 3 times. Yes thats right, 3 times.

> **oldfred said:**
> Some links for repair disks:

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista/7 will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

The run repairs 3 times supposedly works, but even in windows command line works better.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
BootRec.exe /fixmbr

Thank you guys so much, it no loads windows by default and I can now get my 50GB back :).

---

