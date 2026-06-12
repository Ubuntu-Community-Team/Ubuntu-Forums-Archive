---
title: "Different encoding on local computer and shell host"
date: 2009-07-12
forum: General Help
---

### Post by cermei on 2009-07-12
I'm running Debian on my main computer and so does my shell host (using it for irrsi (through screen)). On my local computer, I've set UTF-8 as my locale, but my shell host is using iso8859-1.

The problem is that I can't change the locale on the shell host (by using dkpg-reconfigure) and I don't relly want to change locale from UTF-8 on the local computer. So, is there any way for me to change the locale on the shell host to UTF-8, without super user persmission?
```

Output from locale -a on shell host:
$ locale -a
C
POSIX
swedish
sv_SE
sv_SE.iso88591

Output from locale -a on local computer:
$ locale -a
C
en_US.utf8
POSIX

```Thanks!

---

### Post by miklcct on 2009-07-13
Your shell host does not support UTF-8 according to the output. Sorry, I can't help you except that changing the locale of the shell host to C (which disables all non-ASCII characters) in ~/.profile

export LOCALE=C

---

