---
title: "[MINT] Live CD does not boot, isolinux disk error"
date: 2009-11-09
forum: General Help
---

### Post by DnDer on 2009-11-09
"Loading isolinux: Disk error 6B, AX = 4280, drive 9F

Boot failed: press a key to retry..."



I'm probably just no good at google, but I didn't find any listings for that specific disk error. Many others, but not 6B. Is there a complete index of these errors, so I can go do some research?

---

### Post by jeb800e on 2009-11-09
::deleted::

---

### Post by DnDer on 2009-11-12
<bump>

Did I ask in the wrong Forum? I thought Mint was ubuntu-based... I'll go somewhere else if I was wrong.

---

### Post by dandnsmith on 2009-11-12
> **DnDer said:**
> Did I ask in the wrong Forum? I thought Mint was ubuntu-based... I'll go somewhere else if I was wrong.

No, I think you're in the right place. The silence is probably because nobody so far has any idea what is going wrong (either).

My initial attempts to get round that problem would be
- verify the CD (I think the option is there somewhere on boot)
- try burning another CD after performing an md5sum check on the iso
- suspect that the optical reader is beginning to fail.

HTH

---

### Post by DnDer on 2009-11-12
The iso was burned on a Mac, and I'm attempting to use it on a gateway solo. It could be reasonable that it's starting to fail.

How do I do the checksum?

---

### Post by dandnsmith on 2009-11-13
If you go to the download directory you used for Mint, you should find the various checksums for your release.
Then you need to run the checking for your iso and checksum - details (I'm afraid) depend on which OS you're using - I googled for md5sum when faced with this 'problem' and downloaded appropriate software.

Also thrown up by the google search are pointers to docs.

HTH

---

### Post by DnDer on 2009-11-13
There is no download directory for mint? It's a live CD. I just burned the iso and popped it into the computer in an attempt to make it boot.

I'm obviously missing something important here...

---

### Post by dandnsmith on 2009-11-15
Wherever you got the liveCD iso is where you should find the checksum stuff.

Have a look [here](http://www.linuxmint.com/download.php) - 'hidden' in the link for mirrors torrent and md5 you'll see the checksum value.

---

