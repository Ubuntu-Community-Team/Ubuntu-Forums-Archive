---
title: "Ark: The utility ar is not in your path"
date: 2006-05-29
forum: General Help
---

### Post by pbb on 2006-05-29
Various manuals tell me I should be able to open .deb files in Ark, however when I try that I get this message:

  The utility ar is not in your path.

Does it really mean "ar"? Shouldn't that be "ark"? I've looked in Adept, but there is no "ar" application listed there...

Anybody have any ideas?

---

### Post by kingmonkey on 2006-05-29
which ar
/usr/bin/ar

info ar

 The  GNU  ar program creates, modifies, and extracts from archives.  An
       archive is a single file holding a  collection  of  other  files  in  a
       structure  that  makes  it possible to retrieve the original individual
       files (called members of the archive).

Must exist then.

---

### Post by kzutter on 2006-05-29
It is in the binutils package

---

### Post by Jucato on 2006-05-29
After doing a quick search in Google and in the man pages:

Try installing the *binutils* package.

Hope that helps.

---

### Post by pbb on 2006-05-30
Thanks. That was right, after installing binutils it works. But...

> The GNU assembler, linker and binary utilities
The programs in this package are used to assemble, link and manipulate binary and object files. They may be used in conjunction with a compiler and various libraries to build programs.

That hardly sounds like what I was looking for? I am such a newbie in Linux... How can I solve these things myself? How did you figure out it was connected to binutils?

The two command kingmonkey gave didn't help a bit, **which ar** just did nothing at all, and **info ar** just opened the main info page. Should they have been any help finding out how to find ar?

---

### Post by Jucato on 2006-05-30
> The programs in this package are used to assemble, link and **manipulate binary and object files**.

A .deb file falls under that category, thus the utility ar is rightly found in the binutils package.

How did I find out?
Somewhere in the man page for ar:
> ar is considered a **binary utility** because archives of this sort are most often used as libraries holding commonly needed subroutines.
Then at the bottom:
> SEE ALSO
nm (1), ranlib (1), and the Info entries for **binutils**.

That's basically how I found out. (Although by the time I posted it, kzutter already gave the correct answer :D)

---

