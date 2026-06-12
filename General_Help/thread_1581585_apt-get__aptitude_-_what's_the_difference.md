---
title: "apt-get / aptitude - what's the difference?"
date: 2010-09-25
forum: General Help
---

### Post by leeds_shrew on 2010-09-25
What's the difference between apt-get and aptitude?

Could I use either to effectively update my system? (ie. do "apt-get update" and "aptitude update" do the same thing?)

---

### Post by James78 on 2010-09-25
Apt-get is for command line only, where Aptitude uses a GUI based on ncurses. Ultimately, it doesn't matter, but because apt-get is command line, I use it for command line tasks, and I use aptitude for the GUI tasks.

Yes, you could use both to update the system, and both can also be used for installing, removing, purging, etc, even from the command line.

---

### Post by QLee on 2010-09-25
[QUOTE=James78]Apt-get is for command line only, where Aptitude uses a GUI based on ncurses. Ultimately, it doesn't matter, but because apt-get is command line, I use it for command line tasks, and I use aptitude for the GUI tasks.[/QUOTE]
If you start aptitude from CLI with no arguments it is the text based interface. If you add arguments then it just executes your commands, similar to apt-get.

leeds-shrew,
There are some subtle differences in the two package managers but this thread is not the place to detail all of the differences. You can read about both package managers by entering, man apt-get, and, man aptitude, in a terminal to read the manual page.

Short answer, yes you could use either and some users have a preference for one or the other, or you could the GUIs, software center and synaptic. All of these are higher level interfaces to APT (Advanced Packaging Tool) and all can be used to keep your system upgraded or to install new software.

---

### Post by James78 on 2010-09-25
> **QLee said:**
> **If you start aptitude from CLI with no arguments it is the text based interface. If you add arguments then it just executes your commands, similar to apt-get.**

leeds-shrew,
There are some subtle differences in the two package managers but this thread is not the place to detail all of the differences. You can read about both package managers by entering, man apt-get, and, man aptitude, in a terminal to read the manual page.

Short answer, yes you could use either and some users have a preference for one or the other, or you could the GUIs, software center and synaptic. All of these are higher level interfaces to APT (Advanced Packaging Tool) and all can be used to keep your system upgraded or to install new software.
That's the point I was trying to make. ;)

---

### Post by WorMzy on 2010-09-25
It's worth mentioning that aptitude has been removed from the default installed packages as of 10.10, Maverick Meerkat. You will still be able to install it and use it if you choose to, but apt-get will be the only one of the two available by default.

---

