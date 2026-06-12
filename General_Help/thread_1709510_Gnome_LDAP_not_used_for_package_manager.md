---
title: "Gnome LDAP not used for package manager"
date: 2011-03-18
forum: General Help
---

### Post by skinnyquiver on 2011-03-18
I am using LDAP for authentication but, synaptic and a few other gnome applications ask for a local users password and will not allow you to choose a LDAP user.

I am using the script you find at [http://ubuntuforums.org/showthread.php?t=1656187](http://ubuntuforums.org/showthread.php?t=1656187)

any ideas as to why gnome is not using the LDAP for all authentication and what I should change?

---

### Post by skinnyquiver on 2011-08-01
I figured this out the problem is that the package manager uses policy kit and it only looks in the local admin group for the user list. A simple workaround is to add the user to the local admin group on the computer.

---

