---
title: "How Do I Undelete Files/Folders on a FAT External Hard Drive?"
date: 2012-05-31
forum: General Help
---

### Post by ageofsteam on 2012-05-31
I purged a huge amount of files/folders on my external hard drive, and I accidentally deleted a few things I needed.  I had begun to simply count them as lost, but now it turns out that my sister ALSO needs some things recovered from the drive- and I don't know how to do it.

I'm fairly decent with the terminal, but not a wizard.  Is there some sort of program to view the deleted files/folders and recover some of them?  I've tried the photorec program, and it did almost nothing.

I believe that I may have used the terminal to delete some of the files and folders rm -r, but it's been long enough that I don't recall.

Most of the space freed up by the deletions is still empty, so I don't think that any traces would have been overwritten...

Could someone please help me?

---

### Post by Rodney9 on 2012-05-31
[http://michael-peeters.blogspot.com.au/2012/05/ubuntu-undeleting-files-on-fat.html](http://michael-peeters.blogspot.com.au/2012/05/ubuntu-undeleting-files-on-fat.html)

Good Luck
Rodney

---

### Post by oldfred on 2012-05-31
Testdisk is if it is a deleted partition. But testdisk also includes photorec which can recover more than just photos.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

Some others
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

I have used photorec. It is a long process and does not recover files names just extensions. Photos & music may have internal data you can use to rename.

---

### Post by ageofsteam on 2012-05-31
Thank you. :)  I'll try these (and let you know if they work.)

---

### Post by ageofsteam on 2012-06-09
TestDisk is doing it.  Thank you! :D

---

