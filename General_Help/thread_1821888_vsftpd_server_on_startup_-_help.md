---
title: "vsftpd server on startup - help"
date: 2011-08-09
forum: General Help
---

### Post by olavgal on 2011-08-09
Hello,

I have a vsftpd server running on my ubuntu machine. And I want the server to boot on computer startup, and I made a simple .sh file to add to the startup application list.

```
sudo service vsftpd start
```The problem is, the command needs root, as you can see. Will that work when I boot? If not, how can I get that to work?

---

### Post by dcstar on 2011-08-10
> **olavgal said:**
> Hello,

I have a vsftpd server running on my ubuntu machine. And I want the server to boot on computer startup, and I made a simple .sh file to add to the startup application list.

```
sudo service vsftpd start
```The problem is, the command needs root, as you can see. Will that work when I boot? If not, how can I get that to work?

```
gksudo gedit /etc/rc.local
```

---

