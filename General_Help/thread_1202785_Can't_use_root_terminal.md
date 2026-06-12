---
title: "Can't use root terminal"
date: 2009-07-02
forum: General Help
---

### Post by WIndows to LInux on 2009-07-02
Ever sence I upgraded to the new version of Ubuntu, I can't use the root terminal (the icon does 'gksu gnome-terminal') what happened? not even a new live install cd can do it.

---

### Post by unutbu on 2009-07-02
Open a terminal as a normal user. Type
```

gksu gnome-terminal
```
what is the output?

---

### Post by WIndows to LInux on 2009-07-16
Here is the error output

Failed to contact the GConf daemon; exiting

.....I can still use gksu xterm........

Why does this happen, faulty configuration on Ubuntu, or some sort of security thing that blocks access to a certain file?

---

### Post by CatKiller on 2009-07-16
I don't know what's caused it, but you can always open a normal Terminal window and run ```
sudo -i
``` to have the same effect.

---

### Post by michy99 on 2009-07-16
This is a known bug in Jaunty.

[https://bugs.launchpad.net/ubuntu/+bug/326158](https://bugs.launchpad.net/ubuntu/+bug/326158)
[http://www.linuxformat.co.uk/forums/viewtopic.php?t=10109](http://www.linuxformat.co.uk/forums/viewtopic.php?t=10109)

---

### Post by munky99999 on 2009-07-16
heh i was having the troubles... so instead i was writing bash scripts to do it.

---

### Post by Adiabat on 2009-09-09
Today's update manager run got a new version of gnome-terminal that fixes this problem.

---

