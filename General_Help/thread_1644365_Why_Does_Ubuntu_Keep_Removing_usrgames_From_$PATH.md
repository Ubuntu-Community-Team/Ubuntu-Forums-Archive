---
title: "Why Does Ubuntu Keep Removing /usr/games From $PATH?"
date: 2010-12-13
forum: General Help
---

### Post by Mark76 on 2010-12-13
Stop it. Just bloody well stop it :mad: ](*,)

---

### Post by WorMzy on 2010-12-13
Because you're declaring it on a shell-by-shell basis, maybe?

Try adding it to your .bash_profile file.

[https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables)

---

### Post by Mark76 on 2010-12-13
I don't have shells.

Some of us actually use Ubuntu as a desktop :p

---

### Post by WorMzy on 2010-12-13
Ubuntu doesn't care what you use it as, you always have a shell. ;)

A shell is created for you when you log in via gdm (login screen), and that reads your .bash_profile (as well as /etc/environment) and that creates your PATH variable. If you haven't set PATH to include /usr/games in one of these files, then Ubuntu doesn't know that you want it in your PATH.

---

### Post by Mark76 on 2010-12-13
I shouldn't have to manually set any paths. Nor should Ubuntu remove stuff from $PATH without my permission.

Which it clearly has done.

---

### Post by WorMzy on 2010-12-13
Well, you can continue to complain about it, or you can add the one line to your .bash_profile and be done with it.

Your choice. :)

---

