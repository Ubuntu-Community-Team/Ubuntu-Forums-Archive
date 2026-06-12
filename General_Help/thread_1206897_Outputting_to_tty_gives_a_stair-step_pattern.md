---
title: "Outputting to tty gives a stair-step pattern"
date: 2009-07-07
forum: General Help
---

### Post by DarkNovaNick on 2009-07-07
I'm setting up an application on a server that will rarely have a user interacting with the physical console, but I would like the application to print its log to the console screen so that anyone walking by can see its status.

I normally do something like "tail -f logfile > /dev/tty1" (as root), which has worked fine in the past on RHEL4. However, now on Jaunty the output is kind of "stair-stepped", where it prints one line, then the next line will be indented to the end of the previous line, etc.

The strange thing is, when a user logs on to tty1, the output is fine. It is also fine if you type a username and the console is waiting for you to type in a password. It is only when the console is waiting for a username that the output gets into this "stair-stepped" pattern. I'm guessing the shell goes into a different mode when the username is entered but I can't find where this is or how to configure it so it outputs properly otherwise. Does anyone know? Thanks.

---

### Post by DarkNovaNick on 2009-07-08
If anyone is reading this with the same problem, I solved this by first doing:

stty -F /dev/tty1 opost onlcr


which put the tty1 terminal in the correct mode. Then the stair-stepped pattern no longer occurred.

---

