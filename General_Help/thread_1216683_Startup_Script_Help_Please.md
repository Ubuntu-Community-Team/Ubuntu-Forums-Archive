---
title: "Startup Script Help Please"
date: 2009-07-18
forum: General Help
---

### Post by joeyknuccione on 2009-07-18
SOLVED
I need to do this everytime I start Ubuntu, in order to have the mouse move fast enough:

```

xset m 9 1

```
What I'd like to do is have a script that does this automatically when I start. I'm too noob to experiment (or too scared), and would like to know how to do this without risking damaging my startup.

Thanks in advance for any help.

---

### Post by wojox on 2009-07-18
Did you try System > Preferences > Mouse ?

---

### Post by c0mput3r_n3rD on 2009-07-18
in terminal type gnome-session-properties and add the file.  Make sure it's executable by using the chmod command:
```

chmod u+x fileName

```

---

### Post by joeyknuccione on 2009-07-18
> **c0mput3r_n3rD said:**
> in terminal type gnome-session-properties and add the file.  Make sure it's executable by using the chmod command:
```

chmod u+x fileName

```
But how do I make the file? Just a text editor and enter the commands?

---

### Post by c0mput3r_n3rD on 2009-07-18
> **joeyknuccione said:**
> But how do I make the file? Just a text editor and enter the commands?
Exactly.  A script is just a list of commands, so in your case BASH.
Just put the command in the file, make it executable using the command, and put it with the start up programs

---

### Post by joeyknuccione on 2009-07-18
> **c0mput3r_n3rD said:**
> Exactly.  A script is just a list of commands, so in your case BASH.
Just put the command in the file, make it executable using the command, and put it with the start up programs
'Preciate it, I'm gonna try now...

---

### Post by joeyknuccione on 2009-07-18
> **c0mput3r_n3rD said:**
> Exactly.  A script is just a list of commands, so in your case BASH.
Just put the command in the file, make it executable using the command, and put it with the start up programs
Worked like a charm.

Much Thanks!

---

