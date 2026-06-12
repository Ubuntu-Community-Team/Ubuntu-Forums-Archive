---
title: "permision to make changes"
date: 2009-08-17
forum: General Help
---

### Post by trampintransit2 on 2009-08-17
Hi all

I'm trying to edit xorg.conf, in gedit, but after making a change i am told i dont have permision to do so? what have i done wrong..any ideas?

---

### Post by wojox on 2009-08-17
Open a terminal:

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Mad Hacker on 2009-08-17
in a terminal type
```
sudo gedit PATH_TO_XORG.CONF
```
in the run dialog type
```
gksudo gedit PATH_TO_XORG.CONF
```

---

### Post by newagelink on 2009-08-17
yeah, as they were saying, you need administrator (root) privileges to edit the file .. so "sudo gedit [stuff]" entered in a terminal window runs gedit with administrator privileges (after you enter your password, for which sudo prompts you).

---

### Post by trampintransit2 on 2009-08-17
thanks for that...i stumbled accross a link earlier t omore info about sudo and stuff. cant find it now!....any idea where i can find out more and understand what is all this about sudo and gksudo?

---

### Post by michy99 on 2009-08-17
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

