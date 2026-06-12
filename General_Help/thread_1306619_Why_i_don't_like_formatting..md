---
title: "Why i don't like formatting."
date: 2009-10-30
forum: General Help
---

### Post by 7raTEYdCql on 2009-10-30
I am presently running Intrepid Ibex, and as time has passed i have installed many applications on my machine. Majority of which are available from repositories. 

The point is, that over time, i don't remember all the stuff that i have installed. Is there a script i can generate, so that on my newly formatted machine i can install all the installed applications again. I don't have all my debs stored in apt/cache cause i do a autoclean regularly to free up space.

---

### Post by todak on 2009-10-30
[This page]("http://www.howtoforge.com/record-installed-deb-packages-in-a-text-file-ubuntu-debian") has just what you need! ;)

---

### Post by x C0MMAND0 x on 2009-10-30
Another option is to use APTonCd.  This will allow you to backup all your programs to a file, or to a CD.  Then, you can use APTonCD to re-install all of the same programs.  Keep in mind system type (32bit vs 64bit) as they will not transfer over.

---

### Post by earthpigg on 2009-10-30
> **todak said:**
> [This page]("http://www.howtoforge.com/record-installed-deb-packages-in-a-text-file-ubuntu-debian") has just what you need! ;)

+1

and don't forget to back up your dotfiles in /home for personal settings and whatnot.

---

### Post by 7raTEYdCql on 2009-10-30
Thank you, that was fast!

---

