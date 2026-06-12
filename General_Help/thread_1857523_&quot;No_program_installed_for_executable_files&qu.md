---
title: "&quot;No program installed for executable files&quot;"
date: 2011-10-10
forum: General Help
---

### Post by SkyeFerret on 2011-10-10
I'm trying to install Folding@Home [ [http://folding.stanford.edu/English/LinUNIGuide](http://folding.stanford.edu/English/LinUNIGuide) ] and I get that message when I try to install using the 6.34 file *before* I mark it as executable.
Once I mark it as executable, nothing happens when I try to open / install it - it just sits there. Doesn't show up on System Monitor, either.
Terminal gives me this (already extracted the F@H tar):

```
skye@Skye-Aspire-4520:~$ ls
Audiobooks  Documents  examples.desktop  Music     Podcasts  Templates   Videos
Desktop     Downloads  folding           Pictures  Public    Ubuntu One

skye@Skye-Aspire-4520:~$ cd folding

skye@Skye-Aspire-4520:~/folding$ ls
fah6  FAH6.34-Linux64.tgz

skye@Skye-Aspire-4520:~/folding$ ./fah6 -configonly
bash: ./fah6: cannot execute binary file

skye@Skye-Aspire-4520:~/folding$ ./fah6
bash: ./fah6: cannot execute binary file
```

I haven't tried the 6.02 installer because I don't have a 64-bit OS.

If there's a more appropriate forum for this, feel free to move the thread; I wasn't sure.

Thanks in advance!

EDIT: Fixed, thanks guys!

---

### Post by TeoBigusGeekus on 2011-10-10
Do you get any error messages after you mark it as executable and try to run it?

---

### Post by oldos2er on 2011-10-10
Their instructions say "For 32 bit clients only, use the v6.02 client instead of v6.34" so I'm guessing if you run **file fah6** it will tell you it's 64-bit.

---

### Post by SkyeFerret on 2011-10-11
> **TeoBigusGeekus said:**
> Do you get any error messages after you mark it as executable and try to run it?

Marked as executable, double-click on file: silent failure
Marked as executable, try to run from terminal: No program installed for executable files

> **oldos2er said:**
> Their instructions say "For 32 bit clients only, use the v6.02 client instead of v6.34" so I'm guessing if you run **file fah6** it will tell you it's 64-bit.

```
fah6: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.9, stripped
```

Yeah, 64-bit. Oi. I wish they labeled things a bit clearer.
The 6.02 version looks like it's doing something, so I'll try to get that one working. Thanks, guys. c:

---

