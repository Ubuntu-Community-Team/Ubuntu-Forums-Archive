---
title: "environment variable in a launch button?"
date: 2011-04-30
forum: General Help
---

### Post by olwe on 2011-04-30
I use Emacs and there's a bug that highlights everything whenever you use the ver scroll bar with your mouse. (My bad: Only wimps use Emacs in a window.) The workaround is to start Emacs with this on a command line:

```
$ GDK_NATIVE_WINDOWS=1 emacs
```

where "$" is the shell prompt. Q: how can I put this environment variable in the Emacs lauch icon? Or how/where can I put this in a .bash* file and have it activated (without relogging in)? I've forgotten so much of my Unix cave man skills with Ubuntu. . .

---

### Post by mc4man on 2011-04-30
Don't have emacs but - 
if it has a .desktop (or you create one) then on the Exec= line try something like
```
Exec=env GDK_NATIVE_WINDOWS=1 emacs
```

Otherwise if it was just a cli opening you could make an alias with export instead or possibly a catch all would be a binary diversion of sorts
(if the .desktop isn't suitable I could post an idea there

Edit: sometimes if editing an existing .desktop a log out/in may be required

---

### Post by olwe on 2011-04-30
Sorry I'm still a noob on this sort of hacking: What is a .desktop, where would it be, and what do I want to do with it?

---

### Post by Dave_L on 2011-04-30
The .desktop referred to in the previous post is probably ~/.emacs.desktop.

Alternatively, will it work if it's set it in emacs' startup file ~/.emacs?

```
(setenv "GDK_NATIVE_WINDOWS" "1")
```

---

### Post by mc4man on 2011-04-30
What release of ubuntu are you using and what version of emacs (and did you install from ubuntu repos

(just tried, I'm on natty atm, and I don't see any issue with using mouse on scrollbar with the version available there.
Nor in maverick

---

### Post by olwe on 2011-04-30
Actually, the place I tracked it down said it was a bug that had been fixed in "the latest CVS." I added a bleeding-edge emacs PPA and updated, and that solved the problem. Thanks.

---

### Post by Dave_L on 2011-04-30
Is this the PPA?
[https://launchpad.net/~ubuntu-elisp/+archive/ppa](https://launchpad.net/~ubuntu-elisp/+archive/ppa)

I just noticed I have the same bug with emacs 23.1+1-4ubuntu7.2 on Ubuntu 10.04, so maybe I'll try updating too.

---

### Post by olwe on 2011-04-30
Yes, should be, Dave_L. I upgraded from it and it seems healthy.

---

