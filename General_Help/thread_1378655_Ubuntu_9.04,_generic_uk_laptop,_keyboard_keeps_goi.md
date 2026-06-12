---
title: "Ubuntu 9.04, generic uk laptop, keyboard keeps going mad"
date: 2010-01-11
forum: General Help
---

### Post by john_spiral on 2010-01-11
Hi,

My keyboard layout keeps going mad after a few weeks of usage. If I press the 'j' key for example a number appears?

The problem occured in my main account, I'm logged in with another account and the keyboard is working fine. 

Even changing the keyboard layout doesn't resolve the problem?

If I delete most of the gnome default files it comes back to life.

Why is it happening in the first place? any ideas?

laptop called: Personal Computer No 259EN1, uk keyboard.

/var/log/messages has the following error, not sure it has any bearing:

pulseaudio[6848]: pid.c: Stale PID file, overwriting.

---

### Post by Leppie on 2010-01-11
sounds like the numeric keyboard is on... did you set it to be enabled by default at start up?

---

### Post by john_spiral on 2010-01-11
you're right! Looks like having the Num Lock on makes the layout go crazy!

stupid, I should have solved this one :-/

---

### Post by Leppie on 2010-01-12
well, at least it's working normally now? ;)

---

### Post by john_spiral on 2010-04-30
yes THANKS! Been fine for ages :-)

---

