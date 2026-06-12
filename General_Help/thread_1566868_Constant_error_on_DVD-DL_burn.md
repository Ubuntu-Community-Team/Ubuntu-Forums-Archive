---
title: "Constant error on DVD-DL burn"
date: 2010-09-03
forum: General Help
---

### Post by pcscarpa on 2010-09-03
Hi all

I'm on 10.04.
64bit (but dont think this is 64bit related)

I have been getting this very annoying error while trying to burn DVD-DL media from an iso using growisofs.
Here is the command I used (to burn a backup copy of an xbox360 game)

```
growisofs -use-the-force-luke=dao -use-the-force-luke=break:1913760  -dvd-compat -speed=2.4 -Z /dev/scd0=nameofmyiso.iso
```Now, every single time, usually around 50%, I get this error:

:-[ WRITE@LBA=aacf0h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error

I've been searching around and found threads with people complaining about this error since 2005, but not a single one of them presented any solution (some hint to a kernel issue, which I'd have no idea how to fix. I'm a noob at linux).

I also tried burning it using imgburn under wine, same error, also at 50%.

This is very frustrating, Ive burned around 6 coasters so far and DVD-DL are expensive to keep on this trial and error.

Anyone have any idea on how to fix this?

p.s It's not faulty media before anyone asks. I tried it on Mac and it worked fine. Also, this drive worked well before, before I migrated this machine. Considering this is an error that has been around for some time, I'm pretty sure it's not something hardware related (but ofc, I could be wrong).

---

### Post by pcscarpa on 2010-09-03
no one? =(

---

