---
title: "Why wont Mplayer install"
date: 2006-04-24
forum: General Help
---

### Post by Mikecore on 2006-04-24
Hello Im reloading ubuntu Breezy Badger 5.10 I want to install Mplayer and apt-get 
says its unable to install mplayer. 

Package mplayer-386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer-386 has no installation candidate


Whats up with this anybody know

---

### Post by John64 on 2006-04-24
Make sure your multiverse repositories are enabled.

---

### Post by mjm115 on 2006-04-24
1.  Have you installed all updates?
2. mplayer is in the multiverse repository.  Have you enabled this?

---

### Post by Mikecore on 2006-04-24
Yes I have updated my system and added the correct repo's

---

### Post by f3tus on 2006-04-25
Hey I just reinstalled Kubuntu 5.10 and have the same problem!

---

### Post by aysiu on 2006-04-25
[QUOTE=Mikecore]Yes I have updated my system and added the correct repo's[/QUOTE] Please post the output of this command, then, so that we can double-check: ```
cat /etc/apt/sources.list
```

---

