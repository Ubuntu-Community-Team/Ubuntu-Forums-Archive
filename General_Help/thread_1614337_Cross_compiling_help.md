---
title: "Cross compiling help"
date: 2010-11-05
forum: General Help
---

### Post by nolag on 2010-11-05
I currently have a chroot for 32-bit compiling. I would ultimately like to just use -m32 instead, but when I need packages (in my case lets use GTK's libraries) I only know how to get it by using chroot to the 32-bit then doing apt-get. I am wondering if I can do one of the two following things:
 
1) just tell ubuntu I want to have both the 64 bit and 32 bit version?
2) Can I (safely) just copy the lib in the 32 bit chroot to lib32?
 
The 1st solution is prefered but the second is ok, at least then I would only need to chroot once to get the libs.
 
Also I would love to do the same for ARM/MIPS so I can cross compile with no chroot if possible

---

