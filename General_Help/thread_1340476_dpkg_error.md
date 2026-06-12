---
title: "dpkg error"
date: 2009-11-28
forum: General Help
---

### Post by tlois on 2009-11-28
I downloaded a program that I was going to move to my phone (never tried it before, so don't know why I decided to last night) and now when I try to install anything I get this:

(Reading database ... dpkg: unrecoverable fatal error, aborting:
 files list file for package `com.quickcontacts' contains empty filename
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:


Nothing happens after that.  I have tried quite a few things that I found- none worked.  The last thing I tried was purging com.quickcontacts, but that didn't help, although it did go through some steps after trying to recover.  However, still can't install anything.

Thanks for any help.


SOLVED:  Went into terminal and gksudo nautilus and then deleted all files I had found in searching for com.quickcontacts.  Doh!

---

