---
title: "where is the /etc/X11/xorg.conf file???"
date: 2010-06-09
forum: General Help
---

### Post by bbmak on 2010-06-09
Hi,
I have some display setting in xubuntu 10.04 when I switch from debian to xubuntu. I want to know where is the /etc/X11/xorg.conf ? So, I can copy the debian file to xubuntu.

Anyone knows where is it?

---

### Post by SlidingHorn on 2010-06-09
Chances are there isn't one yet.  You can create it though...

If you have your debian filesystem mounted in ubuntu:

```
sudo cp /path/to/debian/xorg.conf /etc/X11/xorg.conf
```

if not, just:

```
sudo gedit /etc/X11/xorg.conf
```

and paste what you need to in there...save the file and you're set

---

### Post by dino99 on 2010-06-09
actual kernels deals with X, so no need xorg.conf by default

you can create one with: X -configure into a terminal if you need a special config

---

### Post by steveneddy on 2010-06-09
> **bbmak said:**
> Hi,
I have some display setting in xubuntu 10.04 when I switch from debian to xubuntu. I want to know where is the /etc/X11/xorg.conf ? So, I can copy the debian file to xubuntu.

Anyone knows where is it?

That file exists in my Lucid install.

Did you follow that path you posted?

---

### Post by bbmak on 2010-06-09
Yes, I do have it, I actually save the file in my other computer.

---

### Post by bbmak on 2010-06-09
Yes you guys are right. There is no xorg.conf in xubuntu. I just copy the file under /etc/X11, and it works. Thank guys

---

### Post by SlidingHorn on 2010-06-09
no prob...be sure to mark the thread solved if you're satisfied :)

(thread tools @ the top)

---

