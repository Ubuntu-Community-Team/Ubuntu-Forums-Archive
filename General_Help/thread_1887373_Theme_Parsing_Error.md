---
title: "Theme Parsing Error"
date: 2011-11-26
forum: General Help
---

### Post by dRounse on 2011-11-26
I know for a fact this is on another thread because I had this problem before and I found the fix here, but I can't find it again. It currently is not showing up, so it might have gone away when I installed and removed programs. The problem happened when i tried to run a program from the terminal it said something about "Theme parsing error" but the program would run fine. I was just wondering if anyone knows what it was and how to fix it, in case I, or someone else has this problem. Thanks for the help!

---

### Post by raja.genupula on 2011-11-26
How you're launching them from terminal 
i mean actually GUI application have to launch from terminal with **gksu <appname>** command .

so tell me in what way you're launching form terminal.

---

### Post by dRounse on 2011-11-27
> **raja.genupula said:**
> How you're launching them from terminal 
i mean actually GUI application have to launch from terminal with **gksu <appname>** command .

so tell me in what way you're launching form terminal.

So lets say i wanted to run firefox:
david@david:~$ firefox


that usually works fine and it'll run firefox normally, but before it used to say theme parsing error.

---

### Post by raja.genupula on 2011-11-27
yeah , what you got if you launch them with gksu

---

### Post by dRounse on 2011-11-28
> **raja.genupula said:**
> yeah , what you got if you launch them with gksu

I didn't get anything, but when i tried: 
```
gksu gedit
```

it opened gedit but didn't allow me to type, so I went back to the terminal and pressed Ctrl-C and it allowed me to type in gedit.

---

