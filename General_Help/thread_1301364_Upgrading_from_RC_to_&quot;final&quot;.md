---
title: "Upgrading from RC to &quot;final&quot;"
date: 2009-10-26
forum: General Help
---

### Post by jwmollman on 2009-10-26
Hello, I have a quick question. Currently I have the 9.10 RC installed on my EeePC. Once the final release comes out in about a week, could I just do an "aptitude update" to say my system then has the "final" 9.10, or would you recommend doing a fresh install of the final release?

---

### Post by fancypiper on 2009-10-26
When the final release is made, your next update will have you current and you shouldn't have to re-install.

---

### Post by macaholic on 2009-10-26
If you are experiencing no significant issues with the RC, then just keep running normal updares through update manager and you should be good to go.
Additionally, the correct command would either be ```
sudo aptitude update && sudo aptitude safe-upgrade

```
or 
```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by jwmollman on 2009-10-26
Alright, sounds good. And what was the difference between apt-get and aptitude. I never got that. I remember reading somewhere that I should never use them together? I don't know quite what that meant.

---

### Post by macaholic on 2009-10-26
From what I know there isn't much difference other than different commands, for example,```
sudo aptitude remove PACKAGE
``` will remove the specified package and its dependencies that are no longer needed, while ```
sudo apt-get remove PACKAGE
``` will not.
However, the aptitude remove command is replicated in apt get with ```
sudo apt-get autoremove PACKAGE
```
Other than that there's no appreciable difference that I know of.

---

### Post by jwmollman on 2009-10-26
Okay great! I'll just use aptitude from now on, it's a bit less typing to still remove those unneeded packages after an uninstall.

---

### Post by undecim on 2009-10-26
aptitude also have a nice curses interface (if you are willing to read up on it a little)

You can launch it by running aptitude without any arguments. You can also point-click stuff in the gnome-terminal to navigate (if you don't like the keyboard)

---

