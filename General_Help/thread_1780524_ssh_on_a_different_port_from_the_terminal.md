---
title: "ssh on a different port from the terminal"
date: 2011-06-12
forum: General Help
---

### Post by sohlinux on 2011-06-12
I have changed one of my computers ssh servers port to 4003 but how do I use the terminal to connect to it?

normally I just type ssh root@192.168.2.3 and it works but now it doesn't work

I can connect ok with putty because it gives me the option of changing the port number. 

using a terminal how do I change the port I am connecting to? 

ssh root@192.168.2.3 or ssh root@192.168.2.3:4003 doesn't work from the terminal.

---

### Post by sohlinux on 2011-06-12
found it -p

ssh -p 4003 root@192.168.2.3

---

### Post by martinr on 2011-06-12
try:
```
$ssh -p 4003 root@192.168.2.3
```

---

### Post by sohlinux on 2011-06-12
> **martinr said:**
> try:
```
$ssh -p 4003 root@192.168.2.3
```

thx :D

---

### Post by martinr on 2011-06-12
> **sohlinux said:**
> thx :D
You're welcome. We were writing in parallel. After I posted, I saw that you had found it yourself. Good job. 
If you remove SSHD from the standard port you'll have a lot less people knocking on your door. Have fun.

---

### Post by sohlinux on 2011-06-12
> **martinr said:**
> You're welcome. We were writing in parallel. After I posted, I saw that you had found it yourself. Good job. 
If you remove SSHD from the standard port you'll have a lot less people knocking on your door. Have fun.

yep I found it, oh yes it will stop those door knockers ;)

---

### Post by webofunni on 2011-06-12
Please mark the thread solved, if it is fixed

---

### Post by chrisbay90 on 2011-06-12
If you add

```

Host 192.168.2.3
    Port 4003

```

to ~/.ssh/config on the client machine it will use that port by default if not specified otherwise.

---

