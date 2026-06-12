---
title: "Ubuntu startup logo (Urgent)"
date: 2009-07-18
forum: General Help
---

### Post by sreejithbabu on 2009-07-18
I downloaded some packages through the synaptic package manager.
Now the startup Ubuntu logo is changed to a Debian logo.
I want to change it back to the Ubuntu logo.
Does anyone know how to change it through the system settings on the desktop menu bar?
Please it's urgent.

---

### Post by Sidewinder1 on 2009-07-18
If you know what package that you installed that caused the change, just go back into Synaptic and remove it.
HTH,
Side

---

### Post by Sidewinder1 on 2009-07-18
It'll probably requre a re-boot...

---

### Post by Rocket2DMn on 2009-07-18
If you are unsure about what package(s) you installed, you can check /var/log/apt/term.log for a detailed log of all your apt-get commands.  It requires root access to see the file, so try
```
gksudo gedit /var/log/apt/term.log
```
to open the file in a text editor, then scroll down to the bottom.

---

### Post by 3rdalbum on 2009-07-18
You probably installed "usplash-theme-debian". Reinstall "usplash-theme-ubuntu" and your usplash will go back to normal.

(there is a less invasive way of doing this too but I can't remember how it goes, sorry).

BTW, I'm a little surprised that this purely cosmetic problem, that occurs for 30 seconds while booting, is "urgent". If X wasn't working and you needed to get some work done, THAT is urgent.

---

### Post by Sidewinder1 on 2009-07-18
+1 on the "urgency". Guess he/she just wanted a quick response ;-)

---

