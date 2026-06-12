---
title: "unique command?"
date: 2010-11-03
forum: General Help
---

### Post by noloader on 2010-11-03
Hi All,

The unique command is missing. What package should I use for the unique command?  The shell currently suggests John the Ripper.

John the ripper's unique command ([http://manpages.ubuntu.com/manpages/lucid/man8/unique.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/unique.8.html)) is next to useless because it requires an output file name rather than writing to stdout:

jeffrey@studio:~$ cpp -E -dM < /usr/include/stdlib.h | sort | unique
Usage: unique OUTPUT-FILE

---

### Post by noloader on 2010-11-03
I also believe John the Ripper's man page is in the wrong section: it is unique( 8 ) rather than unique( 1 ).

From man man:
       The table below shows the section numbers of the manual followed by the
       types of pages they contain.

       1   Executable programs or shell commands
       2   System calls (functions provided by the kernel)
       3   Library calls (functions within program libraries)
       4   Special files (usually found in /dev)
       5   File formats and conventions eg /etc/passwd
       6   Games
       7   Miscellaneous  (including  macro  packages and conven&#8208;
           tions), e.g. man(7), groff(7)
       8   System administration commands (usually only for root)
       9   Kernel routines [Non standard]

---

### Post by dcstar on 2010-11-03
> **noloader said:**
> Hi All,

The unique command is missing. What package should I use for the unique command?  The shell currently suggests John the Ripper.

John the ripper's unique command ([http://manpages.ubuntu.com/manpages/lucid/man8/unique.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/unique.8.html)) is next to useless because it requires an output file name rather than writing to stdout:

jeffrey@studio:~$ cpp -E -dM < /usr/include/stdlib.h | sort | unique
Usage: unique OUTPUT-FILE

```
man uniq
```

---

### Post by noloader on 2010-11-03
Thank you very much

---

### Post by dcstar on 2010-11-03
> **noloader said:**
> Thank you very much

Please read below:

---

