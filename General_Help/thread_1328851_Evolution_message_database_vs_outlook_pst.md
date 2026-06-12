---
title: "Evolution message database vs outlook pst"
date: 2009-11-16
forum: General Help
---

### Post by walter_j on 2009-11-16
I understand Evolution uses SQLlite database to store messages. How does this format compare to MS Outlooks pst file? I've had issues with outlook when the message file gets very large, and eventually causes problems for outlook. Does Evolution (or Kmail) have the same problems? Or does the SQLlite database bypass this issue?

It would seem to be a real advantage for Evolution over outlook if the database can grow very large w/o issues. I've seem a outlook pst file at 1.7 Gb that caused lots of problems for outlook. I imported the 1.7 Gb file into Evolution in Ubuntu 9.10 without any problem whatsoever (although the Windows version of Evolution had all kinds of problems - unuseable at present).


Walter

---

### Post by dcstar on 2009-11-17
> **walter_j said:**
> I understand Evolution uses SQLlite database to store messages. How does this format compare to MS Outlooks pst file? I've had issues with outlook when the message file gets very large, and eventually causes problems for outlook. Does Evolution (or Kmail) have the same problems? Or does the SQLlite database bypass this issue?

It would seem to be a real advantage for Evolution over outlook if the database can grow very large w/o issues. I've seem a outlook pst file at 1.7 Gb that caused lots of problems for outlook. I imported the 1.7 Gb file into Evolution in Ubuntu 9.10 without any problem whatsoever (although the Windows version of Evolution had all kinds of problems - unuseable at present).


32-bit Evolution had a hard limit of a 2GB file size (64-bit is ok), I don't know if this is fixed now:

[http://ubuntuforums.org/showthread.php?p=8333055#post8333055](http://ubuntuforums.org/showthread.php?p=8333055#post8333055)

---

