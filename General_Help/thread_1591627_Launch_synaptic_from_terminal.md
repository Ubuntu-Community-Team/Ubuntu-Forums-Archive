---
title: "Launch synaptic from terminal"
date: 2010-10-09
forum: General Help
---

### Post by tetris11 on 2010-10-09
Im trying to launch synaptic from the terminal with sudo priveleges, as a keyboard shortcut, but I keep hitting the wall.

Basically all I've got so far is:```
sudo synaptic, password
``` or ```
sudo synaptic:password
```(where password is my password)

but it just keeps asking for my password and ignoring the part where I already typed it```
[sudo] password for user:
``` I suppose it hasn't got there yet, but there must be a way to accomplish this?

Appreciate any help, thanks.

---

### Post by happyhamster on 2010-10-09
Try:
```

gksudo synaptic

```
gksudo is used for graphical applications. For more info, see:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by tetris11 on 2010-10-10
Launched perfectly, thanks!

But still, is there a way to automatically enter my password when performing a sudo command?

---

### Post by lykeion on 2010-10-10
I guess you'll have to create a script file to automatically pass your password. Something like this:
[PHP]#!/bin/bash
echo <your_password> | gksudo synaptic[/PHP]
Save it, make it executable, and maybe put it on your panel.
See here: [https://help.ubuntu.com/community/Beginners/BashScripting#Scripting](https://help.ubuntu.com/community/Beginners/BashScripting#Scripting)

But I wouldn't recommend it. It isn't that difficult entering your password when launching admin applications.
Read more here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tetris11 on 2010-10-10
Thanks man! :guitar:

---

