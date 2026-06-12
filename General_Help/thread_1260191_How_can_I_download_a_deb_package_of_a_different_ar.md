---
title: "How can I download a deb package of a different architecture?"
date: 2009-09-07
forum: General Help
---

### Post by portis on 2009-09-07
Hi all.
I know I can download a deb package by using:
aptitude download xxx

But how can I download a package of a different architecture? By example, if my system is amd64, how can I download a package of i386? 

Thanks.

---

### Post by NoaHall on 2009-09-07
Just download it from the site, and then use "sudo dpkg -i --force-architecture file.deb"

---

### Post by portis on 2009-09-07
Thanks, so there is no way to do this with a single command?

---

### Post by NoaHall on 2009-09-07
That is a single command.

---

### Post by portis on 2009-09-08
Thank you.

I just want the 32bit deb package, not to install it.

---

