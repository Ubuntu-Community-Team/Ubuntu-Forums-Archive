---
title: "bug?"
date: 2009-10-25
forum: General Help
---

### Post by valomer on 2009-10-25
ok so i am the add/remove application to download about 36 new apps (just installed ubuntu on an old laptop) at the same time, i am trying to install wine, so i open the terminal and type in "sudo apt-get install wine". the computer says something like it cannot do that because it is installing something else, and then asks the rhetorical question "is anything else using it?" so me, being annoyed at the moment, typed in yes, and the terminal spazzed out, going for about 100 lines, each line having one "y" on it. it hasn't affected the computer at all, but does anyone have any idea wtf just happened?

---

### Post by lovinglinux on 2009-10-25
Close Add/Remove before trying to install via command-line. You can't use two package managers at the same time. So if you have Add/Remove, Software Center or Synaptic opened, you can run apt-get commands.

---

### Post by cariboo on 2009-10-25
This is not a security question. Moved to General Help

---

### Post by fluffman86 on 2009-10-25
yes is a program.  In a terminal, type

man yes

to read the manual for the program "yes"

---

