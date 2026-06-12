---
title: "[SOLVED] Command like uname to show the distribution name?"
date: 2006-05-23
forum: General Help
---

### Post by bswilson on 2006-05-23
Friends, in my experience, on some UNIX systems, the command **uname -a** shows the operating system's details (I'm thinking of AIX specifically).  However, in Linux, it appears that **uname -a** shows details like the kernel version, etc., but not the distribution name (e.g., *Ubuntu 5.10*):

```
$ uname -a
Linux doctordre 2.6.12-10-386 #1 Fri Apr 28 13:13:44 UTC 2006 i686 GNU/Linux
```

Is there a special command in Ubuntu that does this?

---

### Post by astoltz on 2006-05-23
Is the file /etc/issue what you're after?
```
cat /etc/issue
```

---

### Post by bswilson on 2006-06-02
**astoltz**, yes, that is exactly what I was looking for!  Thanks very much.  For everyone else's benefit, here are some details from the man page entry.

```
ISSUE(5)                   Linux Programmer’s Manual                  ISSUE(5)

NAME
       issue - pre-login message and identification file

DESCRIPTION
       The  file  /etc/issue is a text file which contains a message or system
       identification to be printed before the login prompt.  It  may  contain
       various @char and \char sequences, if supported by getty(1).

FILES
       /etc/issue

SEE ALSO
       getty(1), motd(5)

Linux                             1993-07-24                          ISSUE(5)
```

---

