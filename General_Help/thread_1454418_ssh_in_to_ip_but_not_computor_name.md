---
title: "ssh in to ip but not computor name"
date: 2010-04-14
forum: General Help
---

### Post by spiky001 on 2010-04-14
Hi I have been using ssh but I have to put in the ip address, it wont let me enter the pc name is there any way to do this, it is all on a lan I cant ping the host name either any ideas

---

### Post by ingramproductions on 2010-04-14
Add the hostname to the hostfile

---

### Post by spiky001 on 2010-04-14
thks just what I needed

---

### Post by nothingspecial on 2010-04-14
Add an alias to your .bashrc

for example

To log into my wifes computer, I just type suzie.

```
nano .bashrc
```

Somewhere in that file, add a line like this

```
alias suzie='ssh -X suzie@192.168.1.6'
```

Press Ctrl O to save then Ctrl X to exit.

Then type bash

to restart bash

Then type suzie

obviously, change names and ip addresses accordingly.

---

