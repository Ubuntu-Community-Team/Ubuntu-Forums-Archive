---
title: "testdisk can recover my partition"
date: 2012-05-03
forum: General Help
---

### Post by itcave on 2012-05-03
While installing ubuntu 12.04 I selected to change my ext3 home partition to ext4.  The system let me know that this would require a format, so i swithed it back to ext3, unchecked the format option and let the install continue.  Once finished I realized my data filled Home partition was freshly reformmated. :shock:
 
I've tired Testdisk but neither quick scan nor deep scan found my old partion. 
 
I have run photorec and ertracted some files....
 
Does anyone know of something else to try before I give up? 
 
Thanks

---

### Post by oldfred on 2012-05-03
Testdisk & photorec are the two I have used. Photorec found just about everything I had, including partial & deleted versions of the same file.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)

Always best to have good backups before making major system changes.

---

### Post by itcave on 2012-05-03
The most important file for me is my GNUCASH file.  Does anyone know how I might find a GNUCASH file amoung the 200,000 junk files that PhotoREC pulled out of my drive?

---

### Post by dragonfly41 on 2012-05-04
I suggested use of TEXTstat in this thread ..

[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

to analyse your corpus of 200,000 files created by Photorec (assuming they are text).

[http://neon.niederlandistik.fu-berlin.de/en/textstat/](http://neon.niederlandistik.fu-berlin.de/en/textstat/)

Then apply word frequency list from corpus.

Then search for key words (e.g. GNUCASH) in word frequency list to narrow down your search.

You can also inspect the concordance of words.

...

You could also try**[COLOR=Gray] recoll [/COLOR]**.. install from Synaptic Package Manager

---

### Post by itcave on 2012-05-04
I did some testing and found that the GNUcash files were restored as *.xml.gz files.   I did recover them, but when I try to open them I get the following error:

> No suitable backend was found for file...

any ideas?

---

