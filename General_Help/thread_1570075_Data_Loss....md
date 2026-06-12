---
title: "Data Loss..."
date: 2010-09-07
forum: General Help
---

### Post by Uncas on 2010-09-07
I had a problem ([http://ubuntuforums.org/showthread.php?t=1569556](http://ubuntuforums.org/showthread.php?t=1569556)) which no one can help me, apparently, but there's something interesting happening also.  I had a partition (ext4) (partition #4, 60 Gb, disk 120 Gb) with some movies on it.  Since I had the problem i tried going into that partition, with ubuntu rescue remix and with a kubuntu liveusb, and what I saw was the partition with the files I had like 2 to 3 months ago.  The data that was newer was MIA. Is this strange only to me or are there any known issues like this.
 
Thanks.
 
Uncas

---

### Post by anirudhtomer on 2010-09-08
Once you delete the files only the links to the files are deleted but the actual file still remains on the hard disk. I don't know why your OS is showing you those files since the links must have been deleted earlier.

---

### Post by Uncas on 2010-09-08
Thanks anirudhtomer.  Interestingly enough is that not only I have the old files deleted previously, but I'm also missing the new ones.  It's something like the partition went back in time a couple of months.

---

### Post by Uncas on 2010-09-09
Thanks to everyone who saw this message, especially to Anirudhtomer for replying.  Just for documentation purposes I'm going to explain what I did. 
 
Apparently I encrypted my home folder upon the instalation of ubuntu.  I noticed this because mounting my partition with a LiveUSB Ubuntu Program, all that was inside the home folder was another folder that said Access-Your-Private-Data.desktop.  Sudo-ing into this folder there where a los of folders with encrypted info.  So here comes another problem.  Which was the passphrase used to encrypt the info.  I found a way to recover this info on this link:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
 
With this info I followed the following link:
[http://ubuntuforums.org/showthread.php?t=1534704&highlight=trusted+application+launcher](http://ubuntuforums.org/showthread.php?t=1534704&highlight=trusted+application+launcher)
 
With this I could get to all my data.  I did a backup of what was important and I'm preparing to reinstall the OS.
 
Uncas.

---

