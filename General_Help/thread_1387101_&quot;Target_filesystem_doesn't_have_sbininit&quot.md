---
title: "&quot;Target filesystem doesn't have /sbin/init&quot;"
date: 2010-01-21
forum: General Help
---

### Post by gopchandani on 2010-01-21
Hello All,

There have been many entries about this before but none of them seem to be entailing that what precisely causes this error.

So I downloaded a latest Kernel source from a git and did following in sequence:

1. make
2. make modules
3. make modules_install
4. make install
5. mkinitramfs in /boot
6. update-grub in /boot

Now when I boot in the newly installed kernel option at the grub, with nosplash, I run into following error:

"Target filesystem doesn't have /sbin/init"

I red some other posts and some of them suggested to check disk for any logical errors. Did that too, but the issue seems not be resolved. Any pointers will be highly appreciated on as to what might be causing this and how to resolve this.

Also, I have used the same procedure earlier on Ubuntu 8.10 to compile and install a new kernel, it seems to work. I don't know what has changed between 8.10 and 9.10.

--
Rakesh

---

