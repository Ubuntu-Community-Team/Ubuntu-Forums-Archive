---
title: "Question about SSH and firefox"
date: 2009-10-15
forum: General Help
---

### Post by Renée Jade on 2009-10-15
Hey guys,

I can ssh -X to my university and I've been experimenting with it a bit. I have an alias that opens the session in a new terminal with its own profile, and the profile specifies the the terminal should exit when the command finishes - i.e. when I logout of the SSH session. Now this normally happens as expected, but if I run firefox across the SSH, then close it, then log out, the terminal doesn't close. It's like the process doesn't exit properly if I use firefox. Other X programs don't cause this as far as I can tell. 

The behavior doesn't bother me, but I would love to know why it happens.

Cheers if anyone out there knows :D

---

### Post by matey3 on 2009-10-15
I think firefox stays in the memory as a process after you close it.
If you do a ps ax you'll probably see it in the list.
kill it then exit.

---

### Post by Renée Jade on 2009-10-15
Ohh, fair enough. Thanks! I'll have a squiz next time I'm on Linux. (Currently in one of my rare Vista sessions *blah*). 

Cheers.

---

