---
title: "Recreating /etc/rc?.d"
date: 2006-04-16
forum: General Help
---

### Post by tarkus on 2006-04-16
I'm having a slight issue where due to a failed DMA tranfer, the contents of my /etc/rc?.d directories got dumped in /lost+found.  Most everything else seems to be OK now.  However, I don't know which script goes where!  Of course I could apt-get remove --purge and reinstall all of the packages, but this seems to be overkill (and dangerous to boot).  Is there a way to ask all installed packages to recreate their rc symlinks?

Thanks,
Steven

---

### Post by tarkus on 2006-04-18
Anybody?  I just want a reasonable set of RC scripts!  Right now it does stupid things like trying to start sshd before mounting /usr!  There must be a way to ask dpkg to recreate the rc symlinks, but the documentation says nothing :/

---

