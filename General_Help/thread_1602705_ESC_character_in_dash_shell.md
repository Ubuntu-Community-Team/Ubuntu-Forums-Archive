---
title: "ESC character in dash shell"
date: 2010-10-21
forum: General Help
---

### Post by kfishy on 2010-10-21
Hi all,

This has been bugging me for a while now: when I try to enter an escape sequence in the interactive mode of dash, it keeps on spewing out the <ESC> character as ^[ displayed in plain text instead of catching it as a control character. I vaguely remember encountering this on some UNIX shell but for the life of me I can't find anything on it. So how do I properly enter escape sequences in dash's interactive mode? (it supposedly supports vi line edit mode but I can't access it at all because of the ESC situation)

It's not a make-or-break thing; I usually use bash anyway, but it just kept on nagging in the back of my head... :confused::confused:

Thanks in advance!

---

### Post by Brandon Williams on 2010-10-22
In my experience, dash is just not suitable for interactive use. If it actually worked as the man page says it does, then it would be fine. But it doesn't. Two examples of its shortcomings are command line editing (this simply does not work) and command history (the man page says that the fc builtin exists, but it doesn't). It's perfectly fine for POSIX-compatible scripting support, but trying to use it as an interactive shell will just lead to frustration.

---

### Post by kfishy on 2010-10-23
Thanks for the reply. Yes from reading the man page I got the impression that it's more or less a full fledged POSIX shell ready for everyday use, so I was very confused when I found out otherwise. I actually read a post on a Debian mailing list claiming that dash has more or less all the features one needs in a shell. Must be a different definition of "features" there...

It's good to know that I'm not responsible for all my frustration with dash (well aside from forcing dash do things it can't do in the first place).

---

