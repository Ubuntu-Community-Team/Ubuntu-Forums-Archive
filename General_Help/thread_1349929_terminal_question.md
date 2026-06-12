---
title: "terminal question"
date: 2009-12-08
forum: General Help
---

### Post by skipsbro on 2009-12-08
I've been looking though linux man pages and I see that some commands are named with a number, like:
```
groupdel(8)
```
what exactly does the number mean?

---

### Post by lidex on 2009-12-08
Good question:
[http://ubuntuforums.org/showthread.php?t=538991]("http://ubuntuforums.org/showthread.php?t=538991")
 ```
       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous (including macro  packages  and  conven&#8208;
           tions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

```
Enter:
```
man man
``` in terminal for more (than you ever imagined).

---

