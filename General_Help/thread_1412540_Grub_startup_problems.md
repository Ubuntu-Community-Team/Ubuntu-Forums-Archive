---
title: "Grub startup problems"
date: 2010-02-21
forum: General Help
---

### Post by MegaMoogle on 2010-02-21
I'm currently having problems with actually even starting Ubuntu 9.10. On GRUB 1.97~beta4, I choose the option to start Ubuntu, and I end up getting this warning:

error: no such device: 77d1ba76-0b84-4335-b75e-0d7c5ec5a7b4

I searched through the command line and found this chain of letters in two places.

1:

search --no-floppy --fs-uuid --set 77d1ba76-0b84-4335-b75e-0d7c5ec5a\7b4

2:
linux /boot/vmlinuz-2.6.31-14-generic root=UUID=77d1ba76-0b84-4335-b\75e-0d7c5ec5a7b4 r0 quiet splash

Can someone tell me how to fix this.

Thanks

MegaMoogle

---

### Post by Girya on 2010-02-21
check out post #4 on this thread it seems like the same problem 

[http://ubuntuforums.org/showthread.php?t=1412232&highlight=bare+metal]("http://ubuntuforums.org/showthread.php?t=1412232&highlight=bare+metal")

---

### Post by oldfred on 2010-02-21
Some suggested solutions are here:

Boot Problems:search or no such device
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search)

---

