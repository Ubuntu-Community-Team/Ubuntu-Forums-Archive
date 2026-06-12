---
title: "Alias to exit terminal."
date: 2010-05-09
forum: General Help
---

### Post by duds2008 on 2010-05-09
Hello. Firstly, I apologize that I am in a rush and need to find help fast as my internet usage is about to expire. I have a short cut icon on my panel with the 'terminal' icon on it. I have set the command to gnome-terminal --full-screen for it so that it opens full screen. No problem there. My problem is in trying to make an alias to exit the terminal by adding something like: alias q='exit' in my .bashrc. It doesn't work and I have tried a couple of other ideas but to no avail. Any ideas people? I am at my wits end trying to do this *probably* simple trick. Thanks in advance for any advice you may have to offer me. Take care and peace!
Dudley.
PS: I have read 'man exit' but it doesn't appear to offer too much!

---

### Post by nitstorm on 2010-05-09
in ur home folder create a .bash_aliases file. Better to keep all your alias commands in a separate file as advised in you ~/.bashrc
```

gedit ~/.bash_aliases

*in the file this line should hopefully do the trick:*
alias q='exit'

```
then restart the terminal. The alias command will take effect.

---

### Post by cogier on 2010-05-09
You can exit Terminal with [Ctrl] + D if that helps

---

### Post by jerome1232 on 2010-05-09
Also alt+F4, which is configurable to another key combo in System - Preferences - Keyboard Shortcuts, look under the Window Management section under "Close Window".

---

### Post by duds2008 on 2010-05-09
Thanks guys! I appreciate your help! Brilliant :)

---

### Post by nitstorm on 2010-05-09
No problem. Just mark your thread solved :) Cheers!

---

