---
title: "display progress bar using cp (if possible mv also)"
date: 2010-05-16
forum: General Help
---

### Post by OSXniCKels on 2010-05-16
Hi.

A quick google search gave me a possible answer at this post:
[http://ubuntuforums.org/showthread.php?t=740288](http://ubuntuforums.org/showthread.php?t=740288)

However, this isn't my question exactly.  It sort of is, but the answer is not correct for me.

I'm wondering how to show progress of a cp or mv command.  The man page says -v should do it, but it seems it doesn't show any progress at all.

Is it possible to show progress info with cp or mv?

Or, is there a different command I could use that would show a progress bar.

I know for example scp will show a progress bar, but that is for local-->remote or visa versa, but I'm trying to copy locally.

Thank you for your help.

--OSXniCKels

---

### Post by michy99 on 2010-05-16
Try scp using localhost.```
scp <file> localhost:<destination>
```

---

### Post by OSXniCKels on 2010-05-16
Wow thank you!!  It worked like a charm.

I should have thought of that though, lol.

Thanks again!

--OSXniCKels

---

### Post by coslo on 2010-05-16
Alternatively you can use rsync with the --progress flag

```
rsync --progress <file> <dest>
```

---

### Post by OSXniCKels on 2010-05-16
Sweet!  That one works great as well.  Thanks everyone!

--OSXnCKels

---

