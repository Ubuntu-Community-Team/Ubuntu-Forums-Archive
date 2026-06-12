---
title: "fedora 11 isn't on my grub list how would I add it?"
date: 2009-08-20
forum: General Help
---

### Post by Dustin2128 on 2009-08-20
title says it all, installed fedora 11 KDE from a live disc. I have menu.lst ready to configure. Just tell me what to do.

---

### Post by philcamlin on 2009-08-20
try reinstalling grub :) 
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by running_rabbit07 on 2009-08-20
This [thread]("http://ubuntuforums.org/showthread.php?t=1234034") explains how to add Fedora, scroll to the bottom to see. Worked for me when I installed Fedora.

---

### Post by tgalati4 on 2009-08-20
title Fedora 11
rootnoverify (hd0,3)   (whatever harddisk/partition you put it on)
makeactive
chainloader +1
boot

or

title Fedora 11
rootnoverify (hd0,3)   (whatever harddisk/partition you put it on)
configfile (hd0,3)/boot/grub/menu.lst

Helpful link:
[http://www.linuxjournal.com/article/4622](http://www.linuxjournal.com/article/4622)

Extra points for those who can figure out 2 more ways to do it.

---

