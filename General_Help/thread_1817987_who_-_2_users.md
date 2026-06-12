---
title: "who - 2 users"
date: 2011-08-04
forum: General Help
---

### Post by felipeabrao on 2011-08-04
Hello, everybody!

I am the only user of my laptop, but when I use the comand "who", the result shows 2 users: the TTY of the first one is tty7 and of the other one is pts/0. Both have the same user name (my own name). Is it right? Should not be there just one user?

Thank you in advance,

Felipe

---

### Post by uRock on 2011-08-04
> **felipeabrao said:**
> Hello, everybody!

I am the only user of my laptop, but when I use the comand "who", the result shows 2 users: the TTY of the first one is tty7 and of the other one is pts/0. Both have the same user name (my own name). Is it right? Should not be there just one user?

Thank you in advance,

Felipe

It is normal to have the two listings for one user when using it with a DE.```
uRock   tty7         2011-08-03 16:50 (:0)
uRock   pts/0        2011-08-04 00:01 (:0.0)

```The command ```
man who
``` will print arguments which can be applied for deeper analysis.

---

### Post by sisco311 on 2011-08-04
tty7 is the 7th virtual console. Usually, the X server (GUI) runs on it. pts/0 is a pseudo terminal, most likely the terminal (gnome-terminal?) in which you entered the `who' command.

So yes, the output is normal. You are `logged in' twice, into the GUI and in the terminal.

---

### Post by CatKiller on 2011-08-04
One's you logged in, the other one's the Terminal window you opened to run the command.

---

### Post by felipeabrao on 2011-08-05
OK, thank you all very much!

Felipe

---

### Post by nothingspecial on 2011-08-05
You are not the only user

```
less /etc/passwd
```

There's even a user called nobody.

---

