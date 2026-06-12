---
title: "turn off Compiz via command line"
date: 2009-09-05
forum: General Help
---

### Post by WinterMadness on 2009-09-05
I have to go into ubuntu via terminal mode. A setting in compiz makes the GUI black, and I need to turn it off BEFORE I STARTX.

So, I can login, change the setting and type startx and then it should be off. Thanks

---

### Post by NoaHall on 2009-09-05
killall compiz.real 
startx
Change the setting
compiz.real

---

### Post by c0mput3r_n3rD on 2009-09-05
As well, the command "top" displays all running running processes, and to kill the process; get the id number, and type: kill pid   (pid = process id).  That's just for your future reference.

---

### Post by WinterMadness on 2009-09-05
> **NoaHall said:**
> killall compiz.real 
startx
Change the setting
compiz.real

it says no processes killed. Could this be because x has never started in the first place?

---

### Post by NoaHall on 2009-09-05
Hm, yes. Or maybe compiz runs under a different service name under KDE. Try using "killall" and then start writing "com" and then use tab to see the aviable options.

---

### Post by WinterMadness on 2009-09-05
> **NoaHall said:**
> Hm, yes. Or maybe compiz runs under a different service name under KDE. Try using "killall" and then start writing "com" and then use tab to see the aviable options.

Ah, I forgot to mention, im using my netbook which is using Gnome.

I change the session to be terminal only. Basically, when x starts compiz cannot start with it, the current setting has it set to do so, I need to turn that setting off with the commandline, and x not being started

---

### Post by NoaHall on 2009-09-05
Ah... Try starting x, and then using "alt + ctrl + f2" to get to a terminal, and then do it

---

### Post by WinterMadness on 2009-09-05
> **NoaHall said:**
> Ah... Try starting x, and then using "alt + ctrl + f2" to get to a terminal, and then do it

yup that worked.

did ctrl alt f2, went into terminal did killall compiz.real then typed exit and x restarted without compiz.

thanks a ton dude!

---

