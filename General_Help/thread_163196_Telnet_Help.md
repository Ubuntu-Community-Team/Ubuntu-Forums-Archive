---
title: "Telnet Help"
date: 2006-04-20
forum: General Help
---

### Post by HEHATEME on 2006-04-20
I'm requried to used telnet 4 a test in my class
I install telnetd but I can not use it.
Any suggesstions

---

### Post by cgjones on 2006-04-20
What exactly do you need to do with telnet? Set up a telnet server, or use telnet to log into a remote computer?

---

### Post by aysiu on 2006-04-20
Isn't *ssh* more secure than *telnet*?

---

### Post by cgjones on 2006-04-20
Yes, ssh is more secure then telnet, but you gotta work with what you are given. Sometimes it just isn't right.

---

### Post by Al3xanR0 on 2006-04-20
If you are trying to initiate a telnet session to a windows machine from  your Ubuntu machine, RDP needs to be installed the Ubuntu machine. Here how I did it 

```
apt-get install rdesktop
```

then 

```
rdesktop -a 24bpp -g 1010x645 -x l -r sound:remote <hostname or Ip goes here>:3389
```

g= geometery, adjust as needed, hope that this was useful

---

### Post by cgjones on 2006-04-20
Why would rdesktop need to be installed to use telnet?

---

### Post by Al3xanR0 on 2006-04-20
[QUOTE=cgjones]Why would rdesktop need to be installed to use telnet?[/QUOTE]

It doesn't -this is just an example of its use. Remote desktop uses telent. Perhaps I was unclear on exactly what you telnet issue was other than you "can't use it".

---

### Post by cgjones on 2006-04-20
I'm pretty sure that RDP has nothing to do with telnet. It's a different protocol.

---

