---
title: "Where to find installed applications"
date: 2011-06-20
forum: General Help
---

### Post by Gember on 2011-06-20
I have installed SAFECOPY & TESTDISK using Synaptic manager. after installation I can't find the applications in the menu, I am trying to use them. Any one who can help? where to find these applications? I absolute beginner!

---

### Post by haqking on 2011-06-20
> **Gember said:**
> I have installed SAFECOPY & TESTDISK using Synaptic manager. after installation I can't find the applications in the menu. Any one who can help? where to find these applications? I absolute beginner!

I dont think either have a GUI in linux.

you need to use command line i believe though i may be wrong.

[http://manpages.ubuntu.com/manpages/natty/man1/safecopy.1.html](http://manpages.ubuntu.com/manpages/natty/man1/safecopy.1.html)

---

### Post by yetiman64 on 2011-06-21
I don't know Safecopy at all, testdisk is run in a terminal as root with the command,```
sudo testdisk
``` You may need to resize the terminal window if testdisk refuses to start in a window that is too small IIRC.

Edit:quite a few programs in Synaptic are command line only, if you suspect this is so or can't find a menu entry, then open a terminal and input the program name (note the the terminal is case sensitive and should try all lower case for the names, if it requires root access it will generally tell you so).

Edit 2: just checked safecopy out, it is a  command line tool. Use ```
man <command>
``` for further info on both tools, replace <command> with the tool you specifically want to check out. To exit a manpage in terminal, press the q key on your keyboard.

---

