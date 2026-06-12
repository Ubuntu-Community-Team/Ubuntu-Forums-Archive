---
title: "Trying to install Yorick, matlab like program"
date: 2011-05-12
forum: General Help
---

### Post by RonB123123 on 2011-05-12
Hi. I installed [Yorick]("http://yorick-mb.sourceforge.net/") (it's similar to Matlab) for a job however, when I run it from the command line it gives me this error.

$ yorick
yorick: error while loading shared libraries: libreadline.so.4: cannot open shared object file: No such file or directory

How can I go about getting rid of this error message so I can use this program?

I searched the forums and followed a few suggestions of installing packages but it didn't work.

Thanks,
Ron

---

### Post by RonB123123 on 2011-05-14
bump

---

### Post by RonB123123 on 2011-05-14
Solution:

Install yorick using the readme file, then 

sudo ln -s /lib/libreadline.so.5 /lib/libreadline.so.4
sudo ln -s /lib/libncurses.so.5 /lib/libtermcap.so.2

That should fix the missing libraries.

~Ron

---

