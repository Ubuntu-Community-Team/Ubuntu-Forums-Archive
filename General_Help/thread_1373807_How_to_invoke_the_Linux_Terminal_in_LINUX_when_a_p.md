---
title: "How to invoke the Linux Terminal in LINUX when a process becomes unresponsive?"
date: 2010-01-06
forum: General Help
---

### Post by samezoobi on 2010-01-06
If a process becomes unresponsive in WINDOWS then we press "alt+ctrl+del" to invoke the task manager & then terminate the process.Is there any similar way to invoke the Linux Terminal so that we can end a process by the 'kill' command when it becomes unresponsive?Any help would be gladly accepted.

---

### Post by gaute on 2010-01-06
Hi!

I do this when something locks up on my Ubuntu:

1. Press CTRL +Alt + F1
   (F1 through F6 are all valid for this)
   This takes you to the login prompt on the console
2. Log in as usual
3. type "ps -e"
   This will display the running programs
4. type "killall nameoftheprogram"
   This will kill the running (stuck) program
5. Press CTRL + Alt + F7
   You'll be back at your desktop, and hopefully you've killed the correct program;)

---

### Post by eltama on 2010-01-06
That's what I use too. Ctrl+Alt+F1 to get a terminal, kill the troublesome process and Ctrl+Alt+F7 to get back to Gnome.

Note that you can also do ctrl+alt+del in Ubuntu but it will only give you options to log out, restart, suspend or shut down your computer. You could also associate a key combination to gnome-system-monitor, but usually when a process is unresponsive those key combinations do not work.

---

