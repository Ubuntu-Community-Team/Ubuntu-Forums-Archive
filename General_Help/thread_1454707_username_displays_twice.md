---
title: "username displays twice"
date: 2010-04-15
forum: General Help
---

### Post by dodle on 2010-04-15
If I type in a command in the terminal to display which users are logged on, my username appears twice:```
:~$ users
username username
```
or
```
:~$ who -q
username username
# users=2
```I have only logged in once, why is it showing twice?

Ubuntu 9.10 Karmic

---

### Post by dominiquec on 2010-04-15
The users command shows the number of active sessions to the system.  One refers to your graphical session, the other refers to the terminal session in which you entered your command.

Try this: open another terminal, then run the users command again.  See what comes out.

The who command is more instructive, IMHO.

---

### Post by melrokz on 2010-04-15
Linux is a multiuser operating system. It has 7 'virtual terminals' where 6 are CLI based and 1 is the normal GUI. So, typing Ctrl+Alt+F1 gets you into the 1st terminal....Ctrl+Alt+F6=6th terminal and Ctrl+Alt+F7=GUI mode. Different users can log in and work in each of these terminals.

Now,typing 'who' gives me this output (I'm logged into 2 terminals.)
```

melvin@melvin-desktop:~$ who
melvin   tty1         2010-04-15 10:53
melvin   tty7         2010-04-15 10:39 (:0)
melvin   pts/0        2010-04-15 10:59 (:0.0)

```
tty1 = 1st CLI based terminal.
tty7 = normal GUI interface.
pts/0 = GNOME terminal from which I'm running the command!

I opened another terminal and got this: 
```

melvin   tty1         2010-04-15 10:53
melvin   tty7         2010-04-15 10:39 (:0)
melvin   pts/0        2010-04-15 10:59 (:0.0)
melvin   pts/1        2010-04-15 11:02 (:0.0)

```
Shows that I've 2 terminals open!
Have a nice day!

---

### Post by dodle on 2010-04-15
Interesting, thank you very much.  I thought there was something wrong with my installation.

---

