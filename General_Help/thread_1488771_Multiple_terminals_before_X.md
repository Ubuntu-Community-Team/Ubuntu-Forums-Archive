---
title: "Multiple terminals before X"
date: 2010-05-20
forum: General Help
---

### Post by schoft on 2010-05-20
Hey,

When i start my Ubuntu it doesnt go directly into xserver/desktop mode. This is because my machine is very slow. Therefor i exclusivly use the terminal. I only hate the fact that there is only one terminal and i cant switch between them. ctrl-shift-F2 doesnt work. How can i use multiple terminals before having logged into X?

---

### Post by patchwork on 2010-05-20
CTRL ALT F(1-6) should give you ttys 1-6.

Each of these tty's is a console environment.  


CTRL ATL F7 will go to the X server

---

### Post by jerome1232 on 2010-05-20
Screen.

It's an amazing program, you can have split/multiple Windows. Here is a screenshot of a ssh session, running screen on the ssh server.

You might want to read a short tutorial on using screen before you try it.

---

### Post by exodus_ on 2010-05-20
hey there,

Before you start up Xorg you can switch virtual terminals by pressing ctrl+F2 F3 or so on right up to the max number of terminals your system is set up to use!

If you find you don't have enough or have too many terminals, you can edit the file /etc/default/console-setup

Look for these two line:

```
# Setup these consoles.  Most people do not need to change this.
ACTIVE_CONSOLES="/dev/tty[1-6]"

```

You can modify this as suits your needs!

---

