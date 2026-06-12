---
title: "Detect user logout"
date: 2011-01-18
forum: General Help
---

### Post by HeroesDieYoung on 2011-01-18
I wrote a program that needs to run in the background, every time I login.

I added a line to my .profile file to launch it in the background.  However, it continues to run after my user logs out, and I need it to stop.  I found that a login shell can send SIGHUP to all processes when it closes, but that option is not enabled by default.  I used `shopt -s huponexit` in my .profile file to enable it, but no signal is sent when I logout.

How can I send a signal to the program when the user logs out?  Or, how can the program detect that the user has logged out and terminate?

---

