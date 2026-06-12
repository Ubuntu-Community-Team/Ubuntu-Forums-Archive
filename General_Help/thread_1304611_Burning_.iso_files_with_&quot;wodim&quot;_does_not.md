---
title: "Burning .iso files with &quot;wodim&quot; does not verify :("
date: 2009-10-29
forum: General Help
---

### Post by amn108 on 2009-10-29
I am using "wodim -v -data -speed=4 ubuntu-9.10-desktop-i386.iso" to burn my copy of downloaded .iso image file (md5 hash verifies), but when, after burning (which succeeds, writing 353266 sectors of 2048 bytes each), I try "dd -bs=2048 count=353266 if=/dev/cdrom | md5sum" to verify burned data, it always fails at 353208 "records", quote:

dd: reading `/dev/cdrom': Input/output error
c48ed384adea76249ad983864a6cd7be  -
353208+0 records in
353208+0 records out
723369984 bytes (723 MB) copied, 274.599 s, 2.6 MB/s

The hash is of course wrong, since it does not read 353266x2048 bytes as it has to.
Also there is no problem with either the drive or the media.

Burning the same image with Brasero and doing the same "dd" procedure gives me correct hash and reads all requested data.

Am I using "wodim" wrong? Why wont it work? I like using command line, as I am faster at typing than clicking...

---

