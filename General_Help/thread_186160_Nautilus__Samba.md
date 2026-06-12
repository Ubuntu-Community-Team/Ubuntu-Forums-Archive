---
title: "Nautilus \ Samba"
date: 2006-06-01
forum: General Help
---

### Post by jdavis on 2006-06-01
I am having a problem with Samba after upgrading to Dapper Drake.

After I upgraded to dapper my machine hung during booting for around a minute (On the "Hardware Abstraction Layer" bit) before continuing, when it finally booted it was very sluggish. A quick google showed samba was the problem and by commenting out the share I was mounting from the fstab and rebooting this fixed the boot hang and the sluggish performance.

Unfortunately this means I cannot mount samba shares in ubuntu now, I also cannot access any samba shares at all.

Nautilus gives <"smb:///" is not a valid location."> whenever I attempt access. Although strangely I can access samba shares through Konqueror and other apps, but not through nautilus?

Anyone any ideas?

thanks, Jonathan :)

---

### Post by jdavis on 2006-06-04
[http://www.ubuntuforums.org/showthread.php?t=186127](http://www.ubuntuforums.org/showthread.php?t=186127)

---

