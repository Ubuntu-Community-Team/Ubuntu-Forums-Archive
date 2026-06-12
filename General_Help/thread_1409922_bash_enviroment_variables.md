---
title: "bash enviroment variables"
date: 2010-02-18
forum: General Help
---

### Post by Schinken on 2010-02-18
Hi.

Yesterday, I ran

```
bash -c set > $HOME/.exports

```And now i can't log into Gnome anymore. I get to the logon screen, enter username and password and it just gets me back to the logon screen.

On Safe mode I'm able to log in.


I suppose this is because I used the command above. 

Is there any way to reset this?

System:

Ubuntu 9.10 x64

Edit: I've tried to reinstall bash via synaptic... didn't work.

---

### Post by Brandon Williams on 2010-02-21
I'm not aware of any special purpose for a file called ~/.exports, but there may well be one. If creation of this file is really the problem, then deleting or renaming the file should be enough to restore your logins. If that doesn't help, then take a look in your ~/.xsession-errors file after a failed login to see if there were any relevant error logged. To view that file, press <Ctrl>+<Alt>+F1 to get to a console login prompt.

---

