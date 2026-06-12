---
title: "Ubuntu 11.10 Shutdown very slow"
date: 2012-03-12
forum: General Help
---

### Post by abdulmajid on 2012-03-12
Hi everyone,

I have a Toshiba Satellite C640 running Ubuntu 11.10 with all the updates installed.
The issue is that my computer takes a long time to shutdown. It takes about 45-50 seconds to shutdown. And I believe it's because of an update I did recently...
Any help would be appreciated. 

Thank you.

---

### Post by abdulmajid on 2012-03-12
Bump...bump...bump

---

### Post by winh8r on 2012-03-12
Have a look here:

[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825]("https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/903825")

Hope this helps you

---

### Post by abdulmajid on 2012-03-12
I tried that. Unfortunately it's not working for me. :(

---

### Post by winh8r on 2012-03-12
How quickly does it shutdown if you use :

```
sudo shutdown -P now
```

is it instant?

---

### Post by abdulmajid on 2012-03-12
It took 55 seconds to shutdown with that command.

---

### Post by winh8r on 2012-03-12
here are some things to try.

Firstly make sure all open applications and programs are saved/closed.

1.ensure all external drives etc. are unmounted
2.disconnect from network/internet.

try shutting down with

```
sudo halt
```
and note down result

then try shutting down with
```
sudo init 0
```
and note down result

post results back here.

---

### Post by abdulmajid on 2012-03-12
I disconnected from the network and tried to shutdown with the halt command and the shutdown process froze...it never did shutdown.

However when I tried to shutdown using the init 0 command it took about 30 sec.

Even if i disconnect the computer from the network and disable network manager still i takes 50 seconds to shutdown....:(


Do you want to take a look at log messages etc...?

---

### Post by abdulmajid on 2012-03-15
I have Ubuntu 11.10 64bit running on my desktop PC and laptop. My desktop takes about 20 seconds to shutdown, which is quite normal as it is an old machine...(P4, 2.1GB RAM) However my laptop takes about 50 seconds to shutdown. What could be the problem? I have tried everything but nothing works. :(

---

