---
title: "Bypass Welcome Screen for persistent install?"
date: 2012-09-18
forum: General Help
---

### Post by ChaosChris2009 on 2012-09-18
Have Ubuntu persistent install on a usb

How can I bypass the welcome screen that presents me with the usual try/install options?

12.04

---

### Post by black veils on 2012-09-18
```
sudo apt-get remove ubiquity
```

which means you wont be able to do a normal install, unless you add that package again^ (i think)

---

### Post by ChaosChris2009 on 2012-09-18
> **black veils said:**
> ```
sudo apt-get remove ubiquity
```which means you wont be able to do a normal install, unless you add that package again^ (i think)

Is this the only way to accomplish this?

I meant I just want to disable the welcome screen.

---

### Post by black veils on 2012-09-18
you could try this [http://askubuntu.com/a/47613](http://askubuntu.com/a/47613)  under the** live usb** header. i looked into ways to disable it also and nothing was possible for me, except removing ubiquity.

---

### Post by ChaosChris2009 on 2012-09-18
> **black veils said:**
> you could try this [http://askubuntu.com/a/47613](http://askubuntu.com/a/47613)  under the** live usb** header. i looked into ways to disable it also and nothing was possible for me, except removing ubiquity.

Before I proceed, what is ubiquity and how will affect the os after the change is applied?

---

### Post by black veils on 2012-09-18
ubiquity is just the ubuntu installer, the install wizard. you will be booted directly to the live session (unless you have other configurations for user accounts etc).

if you want to install ubuntu from that persistent drive one day, just install ubiquity again, it should add all necessary parts. when i removed it, i noticed it took another ubiquity package with it, so just make a note, so you can know they are both installed again, if you need to.

---

### Post by Cheesemill on 2012-09-18
Ubiquity is the Ubuntu installation application (the one that runs when you click on the 'Install Ubuntu' icon).

By removing it from the system you bypass the screen that prompts whether to 'Install' or 'Try' Ubuntu.

---

