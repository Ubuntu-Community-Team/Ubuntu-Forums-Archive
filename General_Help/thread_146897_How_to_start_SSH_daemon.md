---
title: "How to start SSH daemon?"
date: 2006-03-19
forum: General Help
---

### Post by Roxxor on 2006-03-19
How do I start SSH server?

I have emigrated from Gentoo (Im still using it too by the way) and there I just have to start sshd. But there is not sshd program so my quesition is how I start a ssh dameon so I can connect to this computer.

---

### Post by alamba on 2006-03-19
In a terminal do:
sudo apt-get install ssh

This should get sshd installed. Check by doing:
/etc/init.d/sshd restart

Another good check would be install nmap and see what ports your computer is listening on. If sshd port is open (22) and you still can't connect then it's a ssh configuration issue. In that case let the forum know.

A

---

### Post by Roxxor on 2006-03-19
I just have /etc/init.d/ssh
not sshd. 

What's wrong?

---

### Post by ranf on 2006-03-19
Just have a look at the file:
```
less /etc/init.d/ssh
```

---

### Post by beeman on 2006-03-19
Afaik there's no SSH server in the default install, so install it using:

 $ sudo aptitude install openssh-server

It'll automatically start then... :)

---

### Post by Roxxor on 2006-03-19
[QUOTE=beeman]Afaik there's no SSH server in the default install, so install it using:

 $ sudo aptitude install openssh-server

It'll automatically start then... :)[/QUOTE]


It didn't. ssh is the only I have in /etc/init.d, not sshd:
```
roxxor@laptop:~$ sudo /etc/init.d/ssh start
 * Starting OpenBSD Secure Shell server...               
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
Disabling protocol version 2. Could not load host key
sshd: no hostkeys available -- exiting.  
                                                                                      [fail]


```

Why does it fail?

---

