---
title: "Display title of running program when using gnome-terminal"
date: 2012-04-12
forum: General Help
---

### Post by unius on 2012-04-12
Hello, I have the same problem. When I use telnet in terminal (bash) I want it's title to be the ip address of the peer I am telneting to (putty style). Can anybody help with this? I have found some answers how to config dynamic terminal title by editing the /etc/bash.bashrc file, uncommenting some lines in it, but it seems not to work correctly.
Thank you in advance

---

### Post by wallaroo on 2012-04-12
You could just launch terminal from a script or from Alt/F2 and add a title and command.

e.g.
```
gnome-terminal -t 10.1.1.4 -e "telnet 10.1.1.4"
```

---

### Post by overdrank on 2012-04-12
Hi and welcome, I have moved your post to it's own thread. :)

---

### Post by unius on 2012-04-16
at last some useful tip :) 
thank you very much :***

---

