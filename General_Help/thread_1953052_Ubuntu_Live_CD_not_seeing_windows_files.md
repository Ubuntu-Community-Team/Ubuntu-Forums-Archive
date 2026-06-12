---
title: "Ubuntu Live CD not seeing windows files"
date: 2012-04-05
forum: General Help
---

### Post by benjjj6 on 2012-04-05
I have booted using an Ubuntu Live CD as my Vista installation hangs after startup, I want to try and copy all files on the drive to an external drive.

The internal drive was partitioned so in vista I had C: and D:, Ubuntu can see all the files on drive D:

But on drive C: all I can see are a few folders such as Boot and $Recycle

C: should have Windows folders and a few documents, why can I not see these inside Ubuntu?

---

### Post by Mark Phelps on 2012-04-05
If the "C" filesystem is corrupted, Linux will have problems mounting the partition and you will have problems seeing the folders and files.

Unfortunately, if that is true, you also will have difficulty booting into Vista to repair that.

What you can try is the following:
1) Keep pressing the F8 key rapidly as you boot Vista
2) This should get you into a safe mode selection screen
3) Choose the option to start a command line
4) Once there, enter the following command "chkdsk c: /f" (without the quotes)

That should repair any errors in the filesystem.

You might then see if Vista will boot.  If not, read through the info on Boot-Repair below because you may be able to use it to repair the Vista boot:

[http://ubuntuforums.org/showthread.php?t=1769482]("http://ubuntuforums.org/showthread.php?t=1769482")

---

### Post by benjjj6 on 2012-04-06
Boot-Repair looks like it is for fixing errors caused by an Ubuntu installation, is that correct? Because I have not installed Ubuntu I was just using it to try and access my drives.

I can not get in to Safe mode at all, pressing F8 (or any other keys, apart from setup) does nothing

Can I run chkdsk on a drive from Ubuntu somehow?

---

### Post by Mark Phelps on 2012-04-06
> **benjjj6 said:**
> Can I run chkdsk on a drive from Ubuntu somehow?

Sorry, no.

If you have access to another MS Windows PC, you should look into downloading and burning a CD of either of the following:
1) EASEUS Partition Master
2) Minitool Disk Wizard

Booting from either of these should allow you to see the MS Windows partitions, any possibly even repair them.

---

