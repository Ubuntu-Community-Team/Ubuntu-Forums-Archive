---
title: "Command line help for a newb."
date: 2011-09-15
forum: General Help
---

### Post by MutantJohn on 2011-09-15
Hello All,

Back in my days of learning the Interactive Data Language, I was unwittingly using emacs and IDL at the same time and I'd very much like to do so again.

From the terminal we were supposed to type something like $emacs and that would open emacs without stripping my ability to input more commands so that I could in turn give the IDL command. So I've tried messing around with a bunch of different characters and so far nothing's worked. 

So I was wondering, anyone know the magical syntax I'm missing here?

---

### Post by gardnan on 2011-09-15
If you want to detach a process from your terminal, add the '&' character at the end of the command. For example:
```
$emacs &
```
Should start Emacs as a process separate from the terminal client you are using.

---

### Post by sisco311 on 2011-09-15
Not sure if you are looking for: [http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement) or [http://aperiodic.net/screen/](http://aperiodic.net/screen/) perhaps both.

---

### Post by MutantJohn on 2011-09-15
Thank you so much. I completely forgot. I remembered that it was teh & key but I forgot you were supposed to put it at the end. Thank you both for your quick replies.

---

