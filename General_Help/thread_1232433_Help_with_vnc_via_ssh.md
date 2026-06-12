---
title: "Help with vnc via ssh"
date: 2009-08-05
forum: General Help
---

### Post by siuchi on 2009-08-05
I need to connect my office desktop from home, and network is so below:

Home PC -----> Internet ---> Office SSH Box -----> Office Desktop.


I use the following command to connect to office ssh box. but my vncviwer does not seems supporting Sock proxy.

"ssh -D5901 'office ssh box IP'"

Anyone know how can i do it? Thanks

---

### Post by siuchi on 2009-08-05
I need to connect my office desktop from home, and network is so below:

Home PC -----> Internet ---> Office SSH Box -----> Office Desktop.


I use the following command to connect to office ssh box. but my vncviwer does not seems supporting Sock proxy.

"ssh -D5901 'office ssh box IP'"

Anyone know how can i do it? Thanks

---

### Post by Hobgoblin on 2009-08-05
I would use...

```
ssh *office_IP* -L 5901:localhost:5901
```

(this will tunnel port 5900 on your home machine to port 5900 on the office ssh server's localhost.

Then connect to localhost:5901 with vnc viewer.

---

### Post by HermanAB on 2009-08-05
Yes, but that will be verrrryyyyy sssllloooooowww...

Instead of tunneling VNC over SSH, you should just use SSH.  It can do everything VNC does, only better.

Ferinstance:
$ ssh -C -c blowfish -X user@server "gnome-panel"

---

### Post by XCan on 2009-08-05
> **HermanAB said:**
> Yes, but that will be verrrryyyyy sssllloooooowww...

Instead of tunneling VNC over SSH, you should just use SSH.  It can do everything VNC does, only better.

Ferinstance:
$ ssh -C -c blowfish -X user@server "gnome-panel"

I always wondered how it can display the current workspaces/desktops as they were left though.

---

