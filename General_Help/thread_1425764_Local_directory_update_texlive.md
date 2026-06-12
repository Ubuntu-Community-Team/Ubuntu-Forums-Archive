---
title: "Local directory update: texlive"
date: 2010-03-09
forum: General Help
---

### Post by sergeprokofiev on 2010-03-09
I've recently had to update my own package blah.cls in the texlive distro on Ubuntu. I duly put it in /usr/local/share/texmf and ran texhash and mktexlsr (the latter just in case). The database has updated: checked with kpsewhich. 

Now the problem: I'm able to compile my Latex file using that package blah.cls only when I run latex (or Kile, or gedit) in sudo mode. When I run it with no sudo, the error is "can't find the package blah.cls" Obviously other files compile nicely, sudo or no sudo.

Any ideas? Couldn't figure the answer after two hours...

---

### Post by sergeprokofiev on 2010-03-12
Problem solved. Foolishly I compiled latex files under sudo...

---

