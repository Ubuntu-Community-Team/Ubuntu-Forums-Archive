---
title: "Recover txt file"
date: 2012-06-21
forum: General Help
---

### Post by gimu on 2012-06-21
Hi,

Couple of weeks ago, I updated by old 11.10 to 12.04 by doing a full new install. I backuped all my files... except some txt files containing quite important notes, or at least important enough for me wanting to recover them. I tried to look on google but most tools to recover files are designed for looking for images or office documents. Plus, the only information I have on those files are there names and their size (3 files of a few kb each). As my hard drive had allways (and still has) a lot of free space (over 90%, yeap 500go is too much for a student machine =) ) I was hoping that the system never had to overwrite it. Even during the quick format done before the setup of my new 12.04.

Thanks in advance to the ones that will help, I would really appreciate solving that, would mean a lot to me.

---

### Post by oldfred on 2012-06-22
Welcome to the forums.

I used photorec to recover some text files. Just that I had saved them many times and it found all the old versions, so I had to do some grepping to find similar files and file comparisons. Never sure I found last saved version, but got most of data back. 

You can specify in photorec which file extensions to recover. It will not make it much faster as it still has to scan entire drive to find anything that looks like a file.

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

Other tools:
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by gimu on 2012-06-22
Thanks for the detailed information, I'll give it a try tonight, once I get back from work ;) I'll let you know how it went.

---

