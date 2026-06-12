---
title: "SSH from a Mac to Ubuntu not working"
date: 2011-09-29
forum: General Help
---

### Post by Winnopeg on 2011-09-29
New Ubuntu user here - installed it on an old netbook of mine a couple days ago. I'm running 11.04, mostly stock packages.

Now correct me if I'm wrong, but setting up Ubuntu to accept incoming SSH connections on my local network should be pretty damn easy. I installed OpenSSH-server, open terminal on my Mac (running Lion, FWIW) and type 'ssh [sysname].local' (easier than typing the IP, but that works too), enter my password and... my password isn't accepted. No matter how many times I try, Ubuntu doesn't seem to accept the pasword I send; I get "Permission denied, please try again." twice, and then "Permission denied, (publickey,password)." the third after which the session is ended. 

Running 'ssh localhost' on the system I'm trying to connect to, that same password is accepted no problem. Just to make sure it's not a network issue, I tried SSH from Ubuntu to my Mac and sure enough, that worked perfectly too (coincidentally, with the same password...).

Searching Google & these forums, I haven't found anyone with such an issue, so it must be something really obvious/trivial. Still, I tried [generating an RSA key]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") as per the Ubuntu documentation and sending that to the Mac; it sent, but I have no idea how to find/use it on the Mac side (and honestly, don't really want to). So that didn't work.

If anyone could suggest a solution (preferably that gets Ubuntu to accept my normal password or removes the password requirement altogether), that would be great!

---

### Post by azmyth on 2011-09-29
How does the remote PC get the proper username? I usually use 'ssh username_of_remote@IP'. I tried it your way and got permission denied since it was using the localhost username not the remote username.

---

### Post by Winnopeg on 2011-09-29
> **azmyth said:**
> How does the remote PC get the proper username? I usually use 'ssh username_of_remote@IP'. I tried it your way and got permission denied since it was using the localhost username not the remote username.
I tried both ways, but since the username on both systems is "Andre" and there's only one account on each, I didn't really think it mattered. But thinking about it for a second, Andre is lower case in ubuntu; specified it as lowercase and boom, [it works]("http://i.imgur.com/J0a6S.png"). D'oh! No wonder I couldn't find anything online that helped. Thanks!

---

