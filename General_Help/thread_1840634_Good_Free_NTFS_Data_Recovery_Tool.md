---
title: "Good Free NTFS Data Recovery Tool?"
date: 2011-09-07
forum: General Help
---

### Post by trackmagic on 2011-09-07
I started installing Ubuntu over my backup hard drive last night. It ruined the data system files so I can't access my drive. 

Does any body know a good tool for getting the data off it? It can be Ubuntu or XP because I still have XP on my desktop (the one I was going to switch over), but I have a Ubuntu on my laptop.

All the ones I found on the internet are like $70 and I don't even know they will work.

---

### Post by nipunshakya on 2011-09-07
> **trackmagic said:**
> I started installing Ubuntu over my backup hard drive last night. It ruined the data system files so I can't access my drive.

Does any body know a good tool for getting the data off it? It can be Ubuntu or XP because I still have XP on my desktop (the one I was going to switch over), but I have a Ubuntu on my laptop.

All the ones I found on the internet are like $70 and I don't even know they will work.

Whose backup HDD are u talking about(desktop or laptop) ? ? ?

Did you install it on your laptop that has ubuntu or on the desktop that has XP? ? ?
please be clear here... were you trying to dual boot on laptop or get just ubuntu in your desktop and remove XP ? ? ?

What method did you apply to install ubuntu ? ? ?

---

### Post by oldfred on 2011-09-08
I have used photorec. Some text files I wanted, it recovered. But I had saved them many times & I recovered many copies, not sure if I ever got the last saved one. Lots of grepping to and comparing files. 

You need lots of room on another drive as it just scans drive for anything that looks like a file. It takes a long time & you do not recover file names, just extensions.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)
[]("http://cinderbox.net/2011/05/12/photorec-digital-picture-and-file-recovery/")

Others:
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

If swap file be sure to use liveCD that does not automount swap. Most do mount swap to speed things up. This one should be ok.
[http://partedmagic.com/doku.php](http://partedmagic.com/doku.php)
[http://ubuntuforums.org/showthread.php?t=1764283](http://ubuntuforums.org/showthread.php?t=1764283)
See post #22 for results from several recovery tools.
[http://ubuntuforums.org/showthread.php?t=1742220](http://ubuntuforums.org/showthread.php?t=1742220)
[http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

---

### Post by Grenage on 2011-09-08
As oldfred suggested, you can use testdisk/photorec, but you'll have to put in a fair amount of time on finding what you want.

A Windows alternative is 'Get Data Back for NTFS', which in my opinion is the best software around for what it does.  I think they have a free trial to show what *can* be recovered, but the software does cost around $70.

Whatever way you go, you'll obviously not want to install _anything_ on the drive from which you're trying to recover data.

---

