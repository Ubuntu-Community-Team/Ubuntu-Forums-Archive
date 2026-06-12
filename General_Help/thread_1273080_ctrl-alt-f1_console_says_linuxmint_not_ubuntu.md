---
title: "ctrl-alt-f1 console says linuxmint not ubuntu"
date: 2009-09-23
forum: General Help
---

### Post by monkeybritt on 2009-09-23
when i enter console mode in ubuntu the title that is displayed says my system is linuxmint version whatever. i tried a mintmenu install and had nothing but problems, updates and apt and such. i may be picking the pepper out of fly poop here but it is really bugging me. thanks in advance to any that can help.:confused:

---

### Post by dcstar on 2009-09-23
> **monkeybritt said:**
> when i enter console mode in ubuntu the title that is displayed says my system is linuxmint version whatever. i tried a mintmenu install and had nothing but problems, updates and apt and such. i may be picking the pepper out of fly poop here but it is really bugging me. thanks in advance to any that can help.:confused:

```
man hostname
```

---

### Post by monkeybritt on 2009-09-23
that just shows my hostname

my problem is what is displayed before that 

it reads

linuxmint gloria x64 edition britt@laptop blah blah 
it should say ubuntu 9.04 jaunty x64 edition

---

### Post by astrakhan on 2009-09-23
sudo nano /etc/issue

change to what you like and then restart

---

### Post by monkeybritt on 2009-09-23
thank that was a little issue that has been bugging me.

---

