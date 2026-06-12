---
title: "Unable to add Firefox 4 PPA to Synaptic"
date: 2011-05-04
forum: General Help
---

### Post by layers on 2011-05-04
I'm on my parents computer, which is running Xubuntu 8.0.1, and for some wierd reason, I cannot add the source. Graphically, it just wont let me apply the change. Terminally, this:
```
ibo@ibo-laptop:~$ sudo add-apt-repository ppa:mozillateam/firefox-stable
[sudo] password for ibo: 
sudo: add-apt-repository: command not found
ibo@ibo-laptop:~$ 


```

I'm having trouble understanding what it is missing. Help me out?

---

### Post by Tim Sharitt on 2011-05-04
Do you mean Xubuntu 8.10? I believe apt-add-repository was added a little more recently (9.10 maybe?). In may be that you are not running a recent enough version of *buntu to have this functionality.

---

### Post by layers on 2011-05-04
So I have to do it all manually?

Yeah, hardy.

---

### Post by layers on 2011-05-04
oki, done. thanks. I would think that since it is old it would have everything on it. I guess they cut the umbilical cord.

---

### Post by Tim Sharitt on 2011-05-04
Yeah, it was all done manually back in those days.

---

### Post by Tim Sharitt on 2011-05-04
Btw, Hardy reaches end of life on May 12 and will receive no further security updates. You may want to think about upgrading.

---

