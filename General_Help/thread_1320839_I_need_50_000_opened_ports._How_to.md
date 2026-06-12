---
title: "I need 50 000 opened ports. How to?"
date: 2009-11-09
forum: General Help
---

### Post by ilna on 2009-11-09
For httpd service testing and benchmarking I need 50 000 simultaneously opened ports. How to permit?

Kubuntu Karmic is in use.

---

### Post by bchurchill on 2009-11-09
I feel like this is similar to the issue of teaching people to login as root:  99% of the time it's not needed, and the 1% of the time it is needed, the person doing it should already know how.

In this case, it is very, very dangerous to open 50,000 ports for one service unless you know what they're all doing.  And if you know what they're all doing, you probably know how to open them.

What you probably want to do is open port 80, because this is the standard http port.  Look in the instructions for your router to route it to your computer and then open the ports in any firewalls you have setup.

---

### Post by ilna on 2009-11-09
Sorry, I must be more precize. I mean opening of local network sockets - both the httpd service as well as a client (ApacheBench) are local. So, I need to overcome opened file count limit. And I'm confused with:


```
~$ which ulimit
~$ sudo which ulimit
~$ ulimit
unlimited
~$ sudo ulimit
sudo: ulimit: command not found
~$
```

---

### Post by bchurchill on 2009-11-09
Ah, that makes sense!  Sorry for the semi-critical post earlier.

I think I'm having the same issue on my box you are: ulimit works for a normal user, but can only decrease the limit.  sudo doesn't work.  However, ulimit seems to work fine from a root shell. 
#ulimit unlimited

don't really know why...

---

### Post by ilna on 2009-11-09
There isn't any need of any "Sorry" as far as it's my fault and my ugly English :-)

---

### Post by ilna on 2009-11-09
Have tried to add

```
me - nofile 50000
```

to

```
/etc/security/limits.conf
```

but still can not open many sockets.

---

### Post by ilna on 2009-11-09
Solved here:

[http://posidev.com/blog/2009/06/04/set-ulimit-parameters-on-ubuntu/](http://posidev.com/blog/2009/06/04/set-ulimit-parameters-on-ubuntu/)

---

