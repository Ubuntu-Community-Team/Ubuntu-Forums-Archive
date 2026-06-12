---
title: "LuckyBackup - Problems and errors"
date: 2010-01-02
forum: General Help
---

### Post by nicknefarious on 2010-01-02
I have been trying for weeks to get luckyBackup to complete a backup of my OS (Karmic 64-bit) for me. I continue to get error messages every time I run it.

I previously had the version from the Ubuntu repository installed and it seemed to almost every time - freeze up - ie the two screens that were opened under luckyBackup would go blank and become unresponsive. Occasionally the time would update it's self, and sometimes the percentage complete but this would go on forever and chew up atleast 100% of one of my two CPU's.

Generally error messages would appear saying that there was no space left on the device. The destination is 1GB bigger than the source drive. And most times I reformatted the destination so it was fresh for the backup - though in practice I don't want to have to do this every time I want to backup.

Also I had system monitor running while the backup was going and even after I aborted the backup (it had stopped due to errors) when I examined the 'file systems' tab under system monitor the drive continued to consume more and more space until it was full. Though no process should have been accessing the destination drive.

I have searched endlessly about luckyBackup but can only find blog after blog of people recommending it and virtually no reports of problems or errors.

I have attached a text file of the error outputs at the end of the last backup run - it failed at 29% saying there was no space left on the device. These are just two parts of the error output.

Any help appreciated,

Thanks,

Nick

---

### Post by 73ckn797 on 2010-01-02
I am using Lucky to do basic folder back-ups with no problems.

You probably need to only back-up the /home folder. That has all of your settings for whatever programs you have installed. It is really no problem to re-install those when you have to do a reload of Ubuntu. Making a separate /home folder is even better. That would be on a separate partition or another drive. I just reloaded Ubuntu on one computer and re-installed the programs I had before with all of my settings intact.

---

