---
title: "help...my console/terminal is messed up!"
date: 2010-07-22
forum: General Help
---

### Post by theOGRE on 2010-07-22
Something is weird with my terminal. 
Anytime I get a console error message while building something, or look  at a man page, I know my console has problems. Everywhere that should  show a back tick (`), or a quote(") I see a lowercase (a) with a (^) on it, followed  by some space. 
eg. from `man grep'

 grep understands two different versions of regular  expression  syntax:
       â€œbasicâ€  and  â€œextended.â€   In  GNU grep,  there  is  no   difference in

ok... that's what it looks like if I copy and paste, but on my term it's  like ' â        basicâ     '.

I can say : echo '`' and it works just fine.
Also, I cannot use the tty's[0-6] if I use usplash. See my other post for info on that: [[COLOR=Blue]Here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1513557")
If i run `man grep' in a tty, it looks fine.
Does anyone know how to fix either of these problems? Any help is greatly appreciated.

---

### Post by theOGRE on 2010-07-27
Anybody got anything? Anyone, please.

---

### Post by prodigy_ on 2010-07-27
Hmm. What does ```
locale
``` command say?

---

### Post by theOGRE on 2010-07-28
LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

Well, all I notice is that everything is in quotes except the first one, and I don't know if LC_ALL should be null. Thanks for responding. Does this give a clue?

---

