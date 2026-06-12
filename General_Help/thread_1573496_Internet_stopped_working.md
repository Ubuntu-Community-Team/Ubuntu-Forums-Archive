---
title: "Internet: stopped working"
date: 2010-09-12
forum: General Help
---

### Post by eveo on 2010-09-12
Wired connection, I rebooted and my internet does not work. Also, nothing is displayed when typing route -n into terminal. I get the internet icon up top right with a red exclamation mark on it too. I'm ready to post any outputs of anything from terminal, help would be greatly appreciated!

EDIT: So magically my internet started working, though route -n returns nothing and I still get the error signal. Also, Pidgin won't login.

EDIT2: Okay so I was fooling with route add and whatnot and somehow manager to get something into route and internet started working again. 
Here's a screenshot anyways:

[IMG]http://i52.tinypic.com/2gv95cx.png[/IMG]

---

### Post by snowman4839 on 2010-09-12
Does "eth0" come up when you type ```
ifconfig
```How about when you type
```
ifconfig -a
```If it does after...
ifconfig -a then type
```
sudo ifconfig eth0 up
```any of that work?

EDIT: alright, good job

---

### Post by eveo on 2010-09-12
> **snowman4839 said:**
> Does "eth0" come up when you type ```
ifconfig
```How about when you type
```
ifconfig -a
```If it does after...
ifconfig -a then type
```
sudo ifconfig eth0 up
```any of that work?

EDIT: alright, good job

No, NOT good job! Yeah they pop up but I have no idea what I did, I just fooled with routes. And yeah, ifconfig brings eth0 and lo up. I don't want these connections to be erased upon reboot. Also my Pidgin won't connect.

---

### Post by JK3mp on 2010-09-12
Pidgin wont connect but you can visit website etc?

---

### Post by eveo on 2010-09-12
> **JK3mp said:**
> Pidgin wont connect but you can visit website etc?

Yes, that is correct.

---

