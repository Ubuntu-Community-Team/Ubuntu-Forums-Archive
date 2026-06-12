---
title: "Connect to shell server; unbind port???"
date: 2011-10-08
forum: General Help
---

### Post by GMVT on 2011-10-08
```
lolol@Kelly:~$ netstat -a | grep 2727
tcp        0      0 *:2727                  *:*                     LISTEN
```I'm a total nub.  I am trying to set up ZNC with my irssi.

```
Server Name:_** X**_**[.FreeBSDShell.com]("http://absinthe.freebsdshell.com/")**
Server IP: **71.x.x.x**
Port(s):   **2727**
```I installed the ZNC on my laptop and ran the znc --makeconf command to configure it.

Now all I really need to know is:  do I need to use port 2727 to connect to the shell?  Or can I use any port I desire? (ex: 666, 10000, 2727, and so on...) 

If I can only use the port 2727, how can I unbind the port?  Everytime I try to configure ZNC I get to the end and then it gives me an error saying the port 2727 is already binded.

---

