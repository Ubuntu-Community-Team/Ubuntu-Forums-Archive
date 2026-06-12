---
title: "Newbie has java questions"
date: 2010-11-27
forum: General Help
---

### Post by TomAnkcorn on 2010-11-27
Heyy its a newbie here :s
I have been having some problems getting jre up and running.
I have tried afew stuff but decided that I would just go and install it, even if its already there...maybe.

this is what I did 
```
tom@tom-desktop:~$ sudo apt-get install sun-java6-plugin sun-java6 fonts
[sudo] password for tom: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6
tom@tom-desktop:~$ 

```
and it cant find its package ;) must be tiny (:( joke is terrible)

but yeah does anyone have any advise :)

oh and btw I am running lucid 
ta lovely's

oops I really am a newbie problem solved it was just me having a blond moment can this be locked or pooped on or what ever  :P

---

### Post by howefield on 2010-11-29
Try enabling the Partner repository and then try.

System > Administration > Synaptic Package Manager > Settings menu >  Repositories > Other Software tab....

Enable the Canonical Partner entry, reload your package lists and try again.

---

