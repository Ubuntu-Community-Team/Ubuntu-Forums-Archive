---
title: "Lost data, accidently reformatted HD"
date: 2012-07-24
forum: General Help
---

### Post by Mrhedges on 2012-07-24
So I have this dell inspiron laptop. running an older version of ubuntu and I loved it then the wifi stopped working. I ended up getting a great deal on a netbook (toshiba) I wanted to put ubuntu on the new machine then transfer all my data over instead I accidently reformted the HD on the dell. ( i know i know i feel pretty stupid) so is it possible to get some of the data off the Dell HD? mostly text files that i never got around to backup ( i know i know another stupid mistake) can anyone point me in the right direction about data recovery? I haven't turned on or really used the dell since the accident so in theory most of the stuff is still on the HD right? the toshiba is still running windows 7 starter and I have a mac desktop g5 (pre intel)

ok thanks everyone!

---

### Post by CaptinGoogle on 2012-07-24
I've used PhotoRec with some success before.

---

### Post by Nixarter on 2012-07-24
> **Mrhedges said:**
> 1.  so is it possible to get some of the data off the Dell HD? mostly text files that i never got around to backup

2.  I haven't turned on or really used the dell since the accident so in theory most of the stuff is still on the HD right?

1.  It depends...

2.  Same as above (for same reasons).  Though I will add that you seem to be getting hdd formatting and "trash bin" emptying mixed up.  For this case it doesn't matter, though.

First and foremost, did you format the drive correctly, or did you do a "quick" format?  If you formatted it correctly, your data is gone.

If you did a "quick" format, most of your data is still probably there.  You need to dd the drive to a new drive, and work off of the copy.  For this, you will need another drive, at least twice the size of the one you are trying to recover.  Then perform all the recovery operations on the copy.  You will want software than can scan for headerless files in the whatever the drive format was of the ubuntu partition (ext3?).  Then wait for ages, then painstakingly recover the files one-by-one.

Have fun!

---

### Post by oldfred on 2012-07-25
If you did not write data, nor repartition, testdisk may show old info. Otherwise     	CaptinGoogle's suggestion of photorec or similar scan tools is about the only choice. 

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

Others:
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by Mrhedges on 2012-07-26
thanks for you help...what do you guys think about professional data recovery ? worth the money?

---

### Post by oldfred on 2012-07-26
Never checked into professional recovery. Often expensive as it is time consuming, I think they first use the same tools we suggested, they may be able to do just a bit more.
Only NSA has the tools to recover just about anything and you cannot afford them. :)

---

### Post by linux_tech on 2012-07-26
testdisk / photorec work great for recovering data.

---

