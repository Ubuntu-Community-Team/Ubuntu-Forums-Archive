---
title: "remote connection install - use"
date: 2010-03-08
forum: General Help
---

### Post by darkangeldz on 2010-03-08
Hi,

i want to rent a machine from a dedicated company. i can use only linux software.

i have used linux in my personal computer so i do not know how to remote it.

how can i connect to the dedicated ? i want to see the desktop as i want to work with it (installing programs and edit). 

can you give me any guide how can i do it?

Regards

---

### Post by cong06 on 2010-03-08
Most likely the company is expecting you to do everything over ssh. I doubt that they would have installed X on it...

Now's as good a time as ever to learn command prompt.

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by darkangeldz on 2010-03-08
Hi, thank you for the reply. as ubuntu have a config about to accept remote connections, is it possible when i will make ssh to connect , to enable the remote connections. with that way i will be able then to log to the server's desktop without ssh.

---

### Post by cong06 on 2010-03-08
It's very possible. You can even set up ssh tunneling so that even if they don't allow other ports out, you can still access the desktop.

I still highly doubt that they have a graphical interface installed though. And most of those dedicated machines don't allow you to install more software on them.

---

### Post by darkangeldz on 2010-03-08
they have many os to install that use unix cores. i will choose ubuntu 9.10.

as you wrote they will not do anything so i must do all bymyself.

can you give me the right command to enable the remote graphical connection and the tunneling?

---

