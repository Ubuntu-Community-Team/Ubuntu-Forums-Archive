---
title: "From normal, to server"
date: 2006-02-22
forum: General Help
---

### Post by kybishop on 2006-02-22
I've got my ubuntu machine up and running, and I've installed a bunch of packages. Everything is great, although I'd like to make my machine more minimalisitc.

What are the optional packages that I could remove to make Ubuntu faster.

For example, what other then gdm can be removed to improve performance. I'm basically trying to get to a server install in terms of base packages, plus the ones i've added.

---

### Post by nanotube on 2006-02-23
well, gdm is really the big thing to worry about. easiest thing to do is to just disable it from starting. 
```
sudo update-rc.d -f gdm remove 
```
should stop it from getting started by default.
you could poke around in your rcX.d dirs to see what you've got, or install the sysv-rc-conf package which would make it easier for you.
but unless you are really hurting for disk space, no need to actually uninstall packages, just tell them not to start on bootup.

---

