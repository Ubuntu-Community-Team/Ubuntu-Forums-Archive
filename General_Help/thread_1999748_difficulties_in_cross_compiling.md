---
title: "difficulties in cross compiling"
date: 2012-06-08
forum: General Help
---

### Post by hwttdz on 2012-06-08
I'm trying to compile coreutils for a machine
uname -a: SunOS mango 5.9 Generic_122300-61 sun4u sparc SUNW,Sun-Fire-V240
config.guess (from most gnu things): sparc-sun-solaris2.9

from my machine, I tried feeding it --host=sparc-sun-solaris2.9 --target=sparc-sun-solaris2.9, but got a "cannot execute binary file" generic error, which is totally unhelpful.  Any thoughts?  The issue is I'm super tight on disk space on the sparc machine, so I'd like to just compile coreutils on a real machine and copy them in.

---

### Post by hwttdz on 2012-09-14
So I was able to compile in a scratch space and then grab the stuff I needed.  Which sort of got me around quota issues.

---

