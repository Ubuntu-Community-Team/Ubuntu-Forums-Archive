---
title: "Question regarding fixing a corrupt NTFS External Drive"
date: 2011-12-21
forum: General Help
---

### Post by AlexOnVinyl on 2011-12-21
So last night Ubuntu froze up on me while copying some files over to my external NTFS Terabyte Hard Drive, and in turn corrupt it.

I ran the ntfsfix on Linux and it seemed to recover most of it, but I was also told to use Windows cmd chkdsk (drive letter): /r to recover any corrupt NTFS disks.  

Since my drive had still been acting funny and it didn't seem as if all the files got recovered, I finally ended up running chkdsk on a windows computer and it said there were still some orphan files on it that it was fixing.

My question is: **Would using windows to recover the NTFS for sure fix whatever corrupt files were still left?**

And help is appreciated, thanks

[IMG]http://a.yfrog.com/img734/4390/cu8xf.jpg[/IMG]

---

### Post by mbuell on 2011-12-21
Short answer - yes. 

Long answer - even fsck and chkdsk do not work 100% of the time. Perhaps 99.99, but not 100%. 

You should be ok. 

However - I wonder about using a single partition - such a large partition - with NTFS. I don't know, but I do know that drive size has been an issue in Windows in many forms - might want to check on that.

---

### Post by LowSky on 2011-12-21
> **mbuell said:**
> 
However - I wonder about using a single partition - such a large partition - with NTFS. I don't know, but I do know that drive size has been an issue in Windows in many forms - might want to check on that.


NTFS works fine for large partitions. FAT does not (but is addressed with exFAT). NTFS does have flaws, like its horrible fragmentation, and on large drives that could be seen as an issue. However NTFS is probably the best option for any hard drive used over multiple OSes due to Windows not having native support for many others.

If you are dealing with only Linux run machines JFS or XFS for a external drive might be perfect. But for universal access NTFS is still the best option, especially if you need to use machines where you cannot install additional software/drivers.

I have found Windows to be nearly amazing in recovering frozen NTFS drives. usually just plugging the drive in has corrected mount errors I may see on a Linux machine.

---

### Post by AlexOnVinyl on 2011-12-21
> **LowSky said:**
> NTFS works fine for large partitions. FAT does not (but is addressed with exFAT). NTFS does have flaws, like its horrible fragmentation, and on large drives that could be seen as an issue. However NTFS is probably the best option for any hard drive used over multiple OSes due to Windows not having native support for many others.

If you are dealing with only Linux run machines JFS or XFS for a external drive might be perfect. But for universal access NTFS is still the best option, especially if you need to use machines where you cannot install additional software/drivers.

I have found Windows to be nearly amazing in recovering frozen NTFS drives. usually just plugging the drive in has corrected mount errors I may see on a Linux machine.


Is there anyway I could use Hiren Boot CD to recover the drive as well? because my old winxp computer I have laying around is going slower than all hell.

-- I found this post here: [http://www.geekstogo.com/forum/topic/231709-how-to-run-chkdsk-on-ntfs-drive-when-i-cannot-boot-windows/](http://www.geekstogo.com/forum/topic/231709-how-to-run-chkdsk-on-ntfs-drive-when-i-cannot-boot-windows/)

and was curious if it was acceptable to use that method, using a recovery disk or recovery console disk iso to repair the NTFS?

---

### Post by AlexOnVinyl on 2011-12-21
Is it that hard to help someone who doesn't know how to fix this?

I have a whole terabyte of music ive been collecting for 4 straight years, and i'm about to lose it all, and everyone is acting like they don't know how to help.

---

### Post by oldfred on 2011-12-22
You do have to run chkdsk until there are no errors as it does not always fix all issues on one pass. One issue with very large drives is just the amount of time it takes to run chkdsk, and if you ever have to run any of the recovery tools like photorec it can take forever.

@AlexOnVinyl
Often best to post your own thread. You can only run chkdsk from a Windows full install or repairCD/USB not one of the upgrades that is not a full install.
I have run chkdsk on my XP install from a Windows 7 repairUSB. It found more issues than the XP chkdsk, but wrote a Windows 7 boot sector, which I then had to repair with different commands.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If chkdsk does not work.
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by AlexOnVinyl on 2011-12-22
> **oldfred said:**
> You do have to run chkdsk until there are no errors as it does not always fix all issues on one pass. One issue with very large drives is just the amount of time it takes to run chkdsk, and if you ever have to run any of the recovery tools like photorec it can take forever.

@AlexOnVinyl
Often best to post your own thread. You can only run chkdsk from a Windows full install or repairCD/USB not one of the upgrades that is not a full install.
I have run chkdsk on my XP install from a Windows 7 repairUSB. It found more issues than the XP chkdsk, but wrote a Windows 7 boot sector, which I then had to repair with different commands.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If chkdsk does not work.
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

So using chkdsk on xp isnt a good idea then?

---

### Post by AlexOnVinyl on 2011-12-22
> **oldfred said:**
> You do have to run chkdsk until there are no errors as it does not always fix all issues on one pass. One issue with very large drives is just the amount of time it takes to run chkdsk, and if you ever have to run any of the recovery tools like photorec it can take forever.

@AlexOnVinyl
Often best to post your own thread. You can only run chkdsk from a Windows full install or repairCD/USB not one of the upgrades that is not a full install.
I have run chkdsk on my XP install from a Windows 7 repairUSB. It found more issues than the XP chkdsk, but wrote a Windows 7 boot sector, which I then had to repair with different commands.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If chkdsk does not work.
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
So, if so happens that recovery of my external drive fails, will chkdsk tell me? even about specific files?

---

### Post by oldfred on 2011-12-22
I am not sure what chkdsk does if it fails. Sometimes it may tell something, but I have not had that issue. XP chkdsk should fix most issues with an XP drive. I was just pointing out that chkdsk can be run from any Windows verison, although all repairs cannot.

If Microsoft's Checkdisk (chkdsk) failed to repair the MFT, run TestDisk, also rebuild boot sector
[http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)

After that the only thing you can do is run the file scan tools. If it was encrypted those do not work (obviously) and only your backups are the way to recover. Hard drive fail, users make mistakes, and external circumstances (power failure, cat/dog pulls plug etc) all cause major corruption. Multiple backups are the best insurance. (Oldfred goes off to do a backup because he does not do them as often as he recommends to others:))

---

