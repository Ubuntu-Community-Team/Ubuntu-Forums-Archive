---
title: "Nautilus crashing on 9.10"
date: 2010-05-23
forum: General Help
---

### Post by tock on 2010-05-23
I installed openshot and afterwards nautilus started crashing.  dmesg is showing "nautilus[3008]: segfault at 7fbc64a45ff8 ip 00007fbc6c83070d sp 00007fbc64a45ff0 error 6 in libc-2.10.1.so[7fbc6c75f000+166000]"

What do I need to do to get nautilus working?

thanks
bryan

---

### Post by tock on 2010-05-28
bump

---

### Post by tock on 2010-06-13
I found this in one of the hundred posts I read and it worked for me.  Hope it helps someone.

rm -r ~/.local/share/gvfs-metadata

---

