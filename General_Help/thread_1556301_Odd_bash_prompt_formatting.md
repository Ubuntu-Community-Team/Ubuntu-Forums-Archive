---
title: "Odd bash prompt formatting"
date: 2010-08-19
forum: General Help
---

### Post by AngeloBear on 2010-08-19
Hi all,

I've run into something odd:
```
jdougher jdougher> cd
jdougher jdougher> echo $PS1
\u \W>
jdougher jdougher>
```For some reason, rather than replacing $HOME with "~", my prompt just displays the name of my home directory.  It's not a huge problem, but any suggestions on how to fix it?

---

### Post by gmargo on 2010-08-19
It works for me (gives a tilde for $HOME).

What is your $HOME set to? I ask because if $HOME is set to "/home/jdougher/" (with a trailing slash), then you'll get what you're seeing.

---

### Post by AngeloBear on 2010-08-20
A-ha!  The trailing slash is what did it.  I had been messing with usermod and put things back wrong.  And here I was all trying to be clever with cd instead of echoing $HOME.

Thanks!

---

