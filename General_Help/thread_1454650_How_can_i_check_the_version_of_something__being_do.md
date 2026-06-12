---
title: "How can i check the version of something  being downloaded through the apt-get?"
date: 2010-04-14
forum: General Help
---

### Post by jorgeguberte on 2010-04-14
I need to install Mercurial, and i want to do it through the shell. Yesterday i tried it, but i got the 1.1.5 version (something like that),but i need the newest version.
How can i check the version of the package being downloaded (or about to be) and/or get the newest version?

---

### Post by clint0n on 2010-04-14
To check which version is in your enabled repositories you can do ```
aptitude show <package>
``` As far as getting the newest possible version you'll probably have to get it through their official website and a lot times they only offer the source code which you'll have to get dependencies for and compile yourself. The cutting edge versions typical aren't in the main repositories since they haven't been thoroughly tested for bugs.

---

### Post by clint0n on 2010-04-14
This is maybe what you are looking for. [http://mercurial.selenic.com/wiki/Download#Linux_.28.deb.29](http://mercurial.selenic.com/wiki/Download#Linux_.28.deb.29)

Choose the version you want. Next scroll to the bottom and choose your architecture (i386 or AMD64). Then pick a server to download the debian package from. You probably want to remove the old version before installing a new one though. (apt-get remove mercurial)

---

### Post by jorgeguberte on 2010-04-14
> **clint0n said:**
> To check which version is in your enabled repositories you can do ```
aptitude show <package>
``` As far as getting the newest possible version you'll probably have to get it through their official website and a lot times they only offer the source code which you'll have to get dependencies for and compile yourself. The cutting edge versions typical aren't in the main repositories since they haven't been thoroughly tested for bugs.

Great. Thank you! :)

---

### Post by jorgeguberte on 2010-04-14
> **clint0n said:**
> This is maybe what you are looking for. [http://mercurial.selenic.com/wiki/Download#Linux_.28.deb.29](http://mercurial.selenic.com/wiki/Download#Linux_.28.deb.29)

Ooh, Mercurial 1.5 is not in the multiverse yet...well, i'll  do it manually then. I need that specific version to run TortoiseHg, and it keeps complaining that it needs 1.5.

---

