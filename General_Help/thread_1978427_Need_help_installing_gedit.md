---
title: "Need help installing gedit"
date: 2012-05-11
forum: General Help
---

### Post by bOgNeR17 on 2012-05-11
I'm trying to install Midori Internet Browser for Lubuntu but I need to install gedit before I can install it. I tried to install gedit and I get the following error:

```
diarmuid@diarmuids-computer:~$ sudo apt-get install gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gedit

```

Can someone help me with this please?

---

### Post by cmont899 on 2012-05-11
Did you do an apt-get update first?

try:

```
sudo apt-get update
sudo apt-get install gedit
```

---

### Post by bOgNeR17 on 2012-05-11
Yes working now, I always forget the simple things when it comes to doing things like this. Thanks I was looking for the guide on the forums for things to do after installing Lubunutu but doesn't seem to be here anymore. :(

---

