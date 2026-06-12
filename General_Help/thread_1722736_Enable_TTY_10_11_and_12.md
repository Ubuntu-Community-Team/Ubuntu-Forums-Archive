---
title: "Enable TTY 10 11 and 12"
date: 2011-04-06
forum: General Help
---

### Post by *PTR on 2011-04-06
Hi.
I work quite a lot in terminal, and I would like to enable more tty's.

I am using Maverick Meerkat .

After reading some about it, it seems that I could copy and rename any 
off tty /etc/init/ttyx.conf (expect tty1 which is special for security mode _and_ normal mode)

But after reboot whit tty12.conf - the screen went wired and a lot of error-messages was all over the screen, so I had to remove it again.



Any ideas.?

---

### Post by uhenninger on 2011-05-10
Simply copying the files won't work. You'll have to edit the newly copied files to match their respective ttys. 

```

exec /sbin/getty -8 38400 tty<YOUR TTY NUMBER>

```

---

