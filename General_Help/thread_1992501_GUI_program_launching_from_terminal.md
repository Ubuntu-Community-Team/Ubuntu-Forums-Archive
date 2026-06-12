---
title: "GUI program launching from terminal"
date: 2012-05-31
forum: General Help
---

### Post by Ohzed on 2012-05-31
besides using ALT+F2, when i launch a GUI application from the terminal, the application seems to be hooked or dependent upon the terminal, for if i close the terminal, it says "There is still a process running in this terminal. Closing the terminal will kill it." I was wondering if there is a command argument you could type in along with the application you want to start that would circumvent this by simultaneously unhooking the process from being dependent on the terminal that's running at the same time as the process, any answers?

---

### Post by Cheesemill on 2012-05-31
Use screen, it's already installed.
[https://help.ubuntu.com/community/Screen](https://help.ubuntu.com/community/Screen)

Basically you run screen then fire up your application. You can then detach from screen and close the terminal, any processes running in your screen session will remain running. You can re-attach to your screen session later if you wish to.

---

### Post by VCoolio on 2012-05-31
Put nohup in front of your usual command, then you can close the terminal.

---

### Post by wallaroo on 2012-05-31
... or append '& exit' to your command and the terminal will nicely close after launching the application.

e.g.
```
gedit & exit
```The '&' disconnects the terminal from the application and 'exit' closes the terminal.

---

