---
title: "charater encoding problem"
date: 2012-09-20
forum: General Help
---

### Post by AlexBooton on 2012-09-20
I have some samba shares used by Windows users.  Some of the file names in those shares have foreign characters like an "a" with 2 dots above.

Linux displays those files with "(invalid encoding)" appended to the file name.  Samba/Windows seems to just substitute a variation on the file name.

The main problem is my backup system (Retrospect) just refuses to operate.  When it hits one of those files it just stops with an error that makes no sense to me "volume structure corrupt duplicate dirid detected" followed by a hex code like 0xffffff

At first, from that message, I thought there was corruption on the drive but by trial and error I found renaming an offending file allowed Retrospect to continue till it hit the next one.

I need to back up my system! and it's not happening. And I don't want to give up on Retrospect.

I'd like to stress that this just started last week.  The files have been there for years! And Retrospect has been working for years.  So something changed.

The only change to the system was a recent security update.  Samba may have been in that update and other packages as well.  I think a kernel update was also included.

Now as I see it, I have two possible solutions:
1. Fix the encoding so it is not seen by Retrospect as corrupt
2. Rename all those files.

Fix 1 would be preferred if I only new how???  Any ideas?

Fix two would be OK if I had some way to find and rename the files.  I don't know how to even find them all.  I tried:
```
locate invalid encoding
``` which found some files with "encoding" in the name but was not limited to "invalid encoding" and in fact found NO files with "invalid"!

I also tried "find ..." with similar lack of success.  

If I can't even find them all I certainly can't fix them.

So, is there a command or script that can find and rename these files by substituting something like "?" for the bad characters?

This is U12.04

Thanks and sorry for such a long post.

Your help is greatly appreciated.

---

### Post by Vaphell on 2012-09-20
find out what the encoding is and use convmv to rename the file(s) to utf8 (most likely used by your system) in linux filesystem.

```
convmv -f <original_encoding> -t utf8 ...
```

---

### Post by AlexBooton on 2012-09-20
> **Vaphell said:**
> find out what the encoding is and use convmv to rename the file(s) to utf8 (most likely used by your system) in linux filesystem.

```
convmv -f <original_encoding> -t utf8 ...
```

Thanks!  That's just what I'll do.

But I think this will continue to occur as Windows users add more files to the shares.

I'd really like to know what caused this to just become a problem when the files have been there for years?

Any ideas on that?

Thanks again.

---

