---
title: "Where is the directory /usr/X11R6 in Ubuntu 9.10?"
date: 2009-11-24
forum: General Help
---

### Post by hilda0717 on 2009-11-24
Hello,
I need several libraries in /usr/X11R6 to use a grafic software.
I installed X-11 common libraries and so on, but I can not
find any directory X11R6 under /usr.
Why there is not in Ubuntu 9.10?
Someone knows how I can solve this problem?
Thanks a lot.

---

### Post by karlson on 2009-11-24
> **hilda0717 said:**
> Hello,
I need several libraries in /usr/X11R6 to use a grafic software.
I installed X-11 common libraries and so on, but I can not
find any directory X11R6 under /usr.
Why there is not in Ubuntu 9.10?
Someone knows how I can solve this problem?
Thanks a lot.

Run
```

locate <library>

```

---

### Post by moravveji on 2010-05-09
Hi. I'm new to this forum, and this is my first query.
actually, I wish to call pgplot form a Fortran code, and display the output as a window.

I guess I have to give a link to X11.
However, there is no X11R6 directory in my /usr or elsewehere, and "locate X11R6" returns null result.

I also have to add that I have some X11 directories, as
ehsan@ehsan:~/Desktop$ whereis X11
X11: /usr/bin/X11 /etc/X11 /usr/lib/X11 /usr/include/X11 /usr/share/X11
But none of them are suitable to give link to.

How can I have X11R6 fully installed?
Thanks in advance.:P

---

### Post by quadproc on 2010-05-09
> **hilda0717 said:**
> Hello,
I need several libraries in /usr/X11R6 to use a grafic software.
I installed X-11 common libraries and so on, but I can not
find any directory X11R6 under /usr.
Why there is not in Ubuntu 9.10?
Someone knows how I can solve this problem?
Thanks a lot.
X11R6 has been obsolete for quite a while; that is why it isn't part of Ubuntu 9.10.

There is a major compatibility issue between X11R6 and the present X11 version.  The two versions behave very differently and are not compatible with each other.  Additionally, there could be a graphics driver issue because the drivers had to change a lot in order to work with X windows so today's drivers do not work with X11R6.

quadproc

---

