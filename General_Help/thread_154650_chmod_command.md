---
title: "chmod command"
date: 2006-04-03
forum: General Help
---

### Post by lex1 on 2006-04-03
does this sound incorrect

sudo chmod ug0+x /etc/qemu-if 

see end of section 8 in the fist post of this thread

[http://www.ubuntuforums.org/showthread.php?t=66694](http://www.ubuntuforums.org/showthread.php?t=66694)

---

### Post by gkiller on 2006-04-03
Maybe it should have been```
sudo chmod ugo+x /etc/qemu-if
```That set's user, group and others permission to execute the file (or change to the directory if it's a dir)

---

