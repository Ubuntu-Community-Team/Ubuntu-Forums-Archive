---
title: "rainlendar fails to install, conky fails to work"
date: 2009-10-12
forum: General Help
---

### Post by TheNessus on 2009-10-12
Using Karmic (ok, I know it's a beta, but still).

downloaded install file for rainlendar from its website. terminal says this on install:

dpkg: unable to read filedescriptor glags for <package status and progress file descriptor>: bad file descriptor



any ideas? thanks.


also - in you've got the time:

and conky... installed it, put .conkyrc in home folder, started conky and I get nothing.
terminal says:
Conky: /home----/.conkyrc: 11: config file error
Conky: border_margin is deprecated, please use window.border_inner_margin instead
Conky: use_spacer should have an argument of left, right, or none. 'yes' seems to be some form of 'true', so defaulting to right.
Conky: one or more $endif's are missing
Conky: forked to background, pid is 10163
---@----lappy:~$ 
Conky: desktop window (1e000a8) is subwindow of root window (13f)
Conky: window type - override
Conky: drawing to created window (0x4800001)
Conky: drawing to double buffer

---

### Post by TheNessus on 2009-10-12
edit: NOTHING can install from a .deb! it all gives the same output as the Rainlendar install did. help?

---

### Post by oldos2er on 2009-10-12
Looks like it's a known bug: [https://bugs.launchpad.net/vte/+bug/388953](https://bugs.launchpad.net/vte/+bug/388953)

---

