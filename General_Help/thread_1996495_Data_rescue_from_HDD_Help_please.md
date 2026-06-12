---
title: "Data rescue from HDD: Help please"
date: 2012-06-04
forum: General Help
---

### Post by astrobob.tk on 2012-06-04
I have a 500GB HDD that I used to use to archive my data (i.e; i didn;t use it everyday; maybe weekly or monthly). That was 2 years ago. At the time, I experienced an incident with it & my laptop; the connection stopped suddenly (most probably due to a usb malfunction).

This incident occurred while I was "moving" data (more accurately small-size pdf's) which lead to their loss; I couldn't find them neither on my system where they were nor on the HDD. This also lead to the loss of other files (image files). The HDD has been lying aside since then. I can't seem to recall well, but it seems now that most of my files are lost (before that I had them all backed up). So in this thread I seek you're help in regard of recovering those files lost (i.e; the pdf files & some images). Would that be possible?

If I haven't explained my self well, please let me know!

Thanks in advance

---

### Post by oldfred on 2012-06-04
Several choices to try, of course if data a valuable you should make a full image copy and work on copy not original.

What format? If NTFS you may need chkdsk or if ext4, e2fsck. But that may just repair issues and copy fragments from a failed copy into temporary locations.

You can try testdisk if you cannot see drive at all. Testdisk also includes photorec. I have used photorec but it is a lot of work. It does a low level scan of drive for anything that looks like a file. It only recovers by extension, not filename. You can restrict what file types to recover but it still takes hours as it is so low level. It recovered for me my text files, but I had saved the same text files many times and it found all the old versions also. It was a lot of work to get to one that was most of the data, but I never knew which was the last saved.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Other tools:
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

