---
title: "Retrieving Files after a Reformat"
date: 2011-01-12
forum: General Help
---

### Post by lonewolfandcub on 2011-01-12
A co-worker was asking me if there was a way to recuperate his child's baptism photos from his HD after it had been reformatted following a crash. I heard that this was possible and even downloaded a few trial programs, but have yet to try them. Does such a program exist within the community? I would really like to help the guy out soany help or info would be appreciated.

---

### Post by Nytram on 2011-01-12
I've not tried it myself but I've heard good things said about [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

### Post by veggen on 2011-01-13
The most important thing to remember is not to write *anything* to that drive before the recovery procedure.
In Windows, I've only used Winhex (free) and it worked very well. In Ubuntu, PhotoRec is *the* way to go.

---

### Post by lonewolfandcub on 2011-01-13
Thanks, I'll give them  a try. Although  I may have some trouble installing the "tarball" file for PhotoRec, I'm not much of a programmer. I'll just dig around the site for the info I need, if not, well, there's always my friends on the forums to help me out.:D

---

### Post by Primefalcon on 2011-01-13
the best tool I've found for data recovery is testdisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by darkhelmetchris on 2011-01-14
I agree with Primefalcon, veggen, and Nytram.  I have used testdisk and PhotoRec many times for such things; the results have ranged from "good job" to "wow that's surprising".

Keeping in mind that ANY disk writes to the drive in question could  overwrite your desired data, so make SURE to use a secondary disk, partition, or  network share to send your recovered data to and leave your original drive read-only (mount it that way if you know how).

PhotoRec is an excellent tool, and it is included on the TestDisk tool set.  It is also included in Ubuntu via the Synaptic Package Manager, or at the shell by:
```
sudo apt-get install testdisk
```
..so you can use your LiveCD or Live USB, install testdisk, and potentially save your recovered files to a new drive (if they are still in good repair)

Good luck!

---

### Post by lonewolfandcub on 2011-01-15
Thanks, I took a look and it seems fairly straightforward, I'm just hoping that there hasn't been anything written over his photos. I did warn him that this may be for naught, that at the price I'm charging ($0), the results may be the same. I have yet to see his computer or even know what the OS might be, probably Vista since it seemed unstable.

---

