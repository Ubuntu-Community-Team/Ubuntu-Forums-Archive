---
title: "Upgrade has erased ALL my documents/pix - how do I restore"
date: 2012-08-28
forum: General Help
---

### Post by RonaHunnisett on 2012-08-28
I have been using Ubuntu for a while on my computer that I use for work (I am a freelance consultant) and have been totally thrilled with how easy it is to use...until today!

I set the latest set of updates to install on Friday as usual - walked away and didn't think any more of it.

When logging on today, I have discovered that the updates have wiped ALL my files (documents AND pictures) from my computer.

Help please!

I need to restore the computer to the settings I had on Friday - I have lost all my work for August and will not be able to bill clients for it without.

Of course, I should have backed it up as I usually do, to a memory stick, but over the past couple of weeks have been super-busy and haven't had time to do so, so bad points to me!

If there's anyone who can help, please please get in touch - I am going crazy here, and am on the verge of a lot of tears!!!

Thanks v much in advance.

---

### Post by Irony on 2012-08-28
The first thing I would do is boot up with the ubuntu live CD and navigate to your home folder on the hard disk (which should show up as a drive in computer) and look for your files.

I very much doubt that an update would erase your files so they should appear via the live CD, you can then back them up to your thumb drive and then try to figure out what is going on.

---

### Post by lukeiamyourfather on 2012-08-28
Updates don't delete files. Something else has happened. Where are the files stored, are they in your home folder, is the home folder on a partition by itself?

---

### Post by oldfred on 2012-08-28
I agree that updates would not delete files. But just in case do not use system but use liveCD. Any system use may overwrite more data.

I did something with links once and lost a folder, found it a couple of years later, buried in root. But I had an older backup and ended up using photorec to find files. Most were text files that I saved often so photorec found all the old copies. Never was sure if I found last saved. Long process, does not recover file names but just by extension or type.

If a partition is missing use testdisk, if files photorec which is part of testdisk.

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

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

---

