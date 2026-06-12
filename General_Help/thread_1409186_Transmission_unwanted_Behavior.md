---
title: "Transmission unwanted Behavior"
date: 2010-02-17
forum: General Help
---

### Post by ethoxyethaan on 2010-02-17
My intentions where to download a file (5GB+) to my desktop, i imported a .torrent file into transmission and after that transmission locks Up / locks up all other processes.

i went investigating and found out before transmission downloads the file it creates a empty dummy file of the same size in the destination folder, when i checked "iotop" for Read/write speeds i noticed that transmission was writing lots of data to the HD during the lockup. (after a few minutes the lockup ends)

i've been using transmission for a long time now and it never did that before. could it be that it has something to do with my home directory being encrypted? has anyone else had this problem before?

thanks for your time.

---

### Post by Charles Kerr on 2010-02-17
> **ethoxyethaan said:**
> My intentions where to download a file (5GB+) to my desktop, i imported a .torrent file into transmission and after that transmission locks Up / locks up all other processes.

i went investigating and found out before transmission downloads the file it creates a empty dummy file of the same size in the destination folder, when i checked &quot;iotop&quot; for Read/write speeds i noticed that transmission was writing lots of data to the HD during the lockup. (after a few minutes the lockup ends)

i've been using transmission for a long time now and it never did that before. could it be that it has something to do with my home directory being encrypted? has anyone else had this problem before?

thanks for your time.

 
 Yes.  Preallocating a file on an encrypted filesystem is pretty slow.  If your encrypted filesystem is supported by glibc's fallocate64() system call, then this will be much faster for you Lucid.

---

### Post by jamesisin on 2010-02-17
I run transmission outside my /home directory tree.  This solves a number of issues and sounds as though it would help with yours.  Can you place your torrent work on a separate drive, for instance?

---

### Post by HappyFeet on 2010-02-17
> **jamesisin said:**
> I run transmission outside my /home directory tree.  This solves a number of issues and sounds as though it would help with yours.  Can you place your torrent work on a separate drive, for instance?

I agree with this, and do the same.

---

### Post by ethoxyethaan on 2010-02-18
Yes now that i think of it, i've always used transmission outside my home directory for large files. so this might just be the case. 

Creating the empty files should not make transmission lock up tough.

---

### Post by jamesisin on 2010-02-18
I don't experience any lock up from large files (and I've done a few), but I'm not using encryption on /home either.

---

### Post by the_mechanic on 2010-02-28
I am experiencing the same problem. I'm running Ubuntu 9.10 Karmic, transmission 1.75 (9117) and my home dir is encrypted. I tried to download a large file (over 5 gig) via torrent and transmission took over 90% cpu and became unresponsive for several minutes.

---

### Post by jamesisin on 2010-02-28
It sounds as though you should look into filing a bug report (or at least searching to see if a bug report has already been filed) for this.

---

