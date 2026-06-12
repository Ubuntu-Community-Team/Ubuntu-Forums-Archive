---
title: "run a program as root"
date: 2012-08-17
forum: General Help
---

### Post by Spae on 2012-08-17
How can i do this

heck, how can i even run an app from the command line?

---

### Post by Lars Noodén on 2012-08-17
ctrl-alt-T will get you the terminal.  From there, type in the name of the program.  If you want to run it with escalated privileges then use [sudo](http://manpages.ubuntu.com/manpages/karmic/en/man8/sudo.8.html).

What program are you trying to run or which task are you trying to accomplish?  Having a few of those details will help provide examples.

---

### Post by raja.genupula on 2012-08-17
+1 .

for simple ..place **sudo** before what you want to run as root . other wise type as ```
sudo -i 
``` then give the password .
then try to run what you want to do as root .

---

### Post by kemtnbkr on 2012-08-17
If it is a graphical program, make sure to use gksudo to preface it.

For example, to run your file manager (assuming you're running default Ubuntu) as root (be careful, you can delete anything as root!!) you would type:

```
gksudo nautilus
```at the command prompt (terminal)

---

### Post by QIII on 2012-08-17
If you are running a graphical application, use "gksudo".

---

### Post by Deepak J on 2012-08-17
whatever prgm you run as root be very careful..

it can alter the very basic components of the syst

---

### Post by BrianBlaze on 2012-08-17
To emphasize how important this is... what are you trying to run graphically as root?

---

### Post by Khal1d on 2012-08-17
"IF" you are trying to run in graphically that is...

Though knowing a bit more on what exactly you are trying to achieve could be useful...

---

### Post by Scott Harrison on 2012-08-17
Whatever it is, perform a backup first. You can quite easily break your system as the root user.

---

