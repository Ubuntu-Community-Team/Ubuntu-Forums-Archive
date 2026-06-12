---
title: "Problems with Session?  Logs me out"
date: 2011-06-29
forum: General Help
---

### Post by Mr. Monkey on 2011-06-29
I will admit I am still very new with Linux and still need to figure out a lot of the basics.  But here's my problem.  This has only happened  a couple times so far.  I was doing a couple of things and then my X session closed, and it took me to a loading screen, and then flashed, and then restarted X.  So it completely logged me out and I lost what I was doing.  I'm poking through /var/log to see what caused it to happen... but I have no idea where to look.  Is there somewhere specific I should look or look for?

Thank you.

---

### Post by Habitual on 2011-06-30
terminal> 
```
less ~/.xsession-errors
```

You can rename this file also as it may be quite large and on the next "event", then check the smaller-sized version of .xsession-errors

---

