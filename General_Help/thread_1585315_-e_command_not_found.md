---
title: "-e: command not found"
date: 2010-09-30
forum: General Help
---

### Post by kerristallax on 2010-09-30
Set up my laptop as a dual boot with XP and Ubuntu 10.4 64-bit recently, and when I open the terminal (gnome-terminal) it immediately shows 

-e: command not found
chris@lois571:~$ 

Why the -e: command not found in a new terminal window?  It happens every time.  Any ideas?

---

### Post by sisco311 on 2010-09-30
Search the bash initialization and sturtup files for -e and delete it.

What's the output of:
```
grep -A1 -B1 -- -e ~/.profile ~/.bashrc ~/.bash_profile
```?

---

### Post by SlugSlug on 2010-09-30
> **sisco311 said:**
> Search the bash initialization and sturtup files for -e and delete it.

What's the output of:
```
grep -A1 -B1 -- -e ~/.profile ~/.bashrc ~/.bash_profile
```?


cool A1  & B1  never knew abourt that,  whats the two --  for after B1?

---

### Post by sisco311 on 2010-09-30
> **SlugSlug said:**
> whats the two --  for after B1?

-- means end of options, otherwise -e would be treated as an option and not a pattern.

---

### Post by SlugSlug on 2010-09-30
> **sisco311 said:**
> -- means end of options, otherwise -e would be treated as an option and not a pattern.


cool , & why use -e  not just e

---

### Post by kerristallax on 2010-10-04
the second to last line in ~/.bashrc was just "-e"
I deleted that line, and the warning is gone now

---

### Post by sisco311 on 2010-10-04
Cool!

Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

