---
title: "Need source for UNIX shred"
date: 2011-09-21
forum: General Help
---

### Post by MG&amp;TL on 2011-09-21
Hi, I need the source code of the UNIX command "shred" for a project I'm helping with, is there somewhere I can get it?
I have tried 

```
apt-get source shred
```

Which gives 'found no package' on 10.04

and Google.

Ideas?

---

### Post by WorMzy on 2011-09-21
That's because there is no such package as shred. Shred is part of the coreutils package. You might be able to download the coreutils source with apt-get, but here's a link to the project homepage just in case: [http://www.gnu.org/s/coreutils/](http://www.gnu.org/s/coreutils/)

---

### Post by Slim Odds on 2011-09-21
shred is part of a package called coreutils

Try that instead...

---

### Post by MG&amp;TL on 2011-09-21
Ah. Thanks guys. This is what forums are for! :D

---

### Post by patryk77 on 2011-09-21
Bonus tip: You can use dpkg to find which package it belongs to

```
dpkg -S `which shred`
coreutils: /usr/bin/shred
apt-get source coreutils
```

;)

---

### Post by haqking on 2011-09-21
> **MG&TL said:**
> Hi, I need the source code of the UNIX command "shred" for a project I'm helping with, is there somewhere I can get it?
I have tried 

```
apt-get source shred
```

Which gives 'found no package' on 10.04

and Google.

Ideas?

taken from [http://www.perpetualpc.net/srtd_shred.html](http://www.perpetualpc.net/srtd_shred.html)

[s]This uses many overwrite passes, with the data patterns chosen to
maximize the damage they do to the old data.  While this will work on
floppies, the patterns are designed for best effect on hard drives.
For more details, see the source code and Peter Gutmann's paper `Secure
Deletion of Data from Magnetic and Solid-State Memory', from the
proceedings of the Sixth USENIX Security Symposium (San Jose,
California, 22-25 July, 1996).
[The paper is also available online]("http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html").[/s]

hope this helps

edit: actually it appears that was wrong, sorry ;-)

---

### Post by searchfgold6789 on 2011-09-21
There are excellent shredding tools on sourceforge too, for example [freeshred]("http://sourceforge.net/projects/freeshred/").
EDIT: reread your post, this info was not probably necessary sorry!

---

### Post by MG&amp;TL on 2011-09-21
1. Cool. Thanks patryk!
2 & 3. Never mind, I do that all the time. Probably more often than I get something wrong, which is often. :)

And hey, haqking. How did the membership go?

---

