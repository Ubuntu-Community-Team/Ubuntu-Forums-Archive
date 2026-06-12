---
title: "Grub options after installing win7 + uninstall"
date: 2010-05-25
forum: General Help
---

### Post by WannabeFantasma on 2010-05-25
Hi all,

Not sure if it's in the right forum section, but it has nothing to do with Ubuntu..

So I installed Win 7 to test if it was the right CD-key, first full install than you have to enter cd key...

Before the win7 install it had Win Vista + Ubuntu 10.04, installed win7 on ubuntu 10.04 partion

After the test i installed Ubuntu 10.04 
But now in Grub I get : 
Ubuntu Kernel...
Recovery...
Windows

When I press windows I can choose between win 7 and Vista, but I only have vista(previously only win Vista Option), what can I do that it only shows Vista?


Thanks for the help!
Me

---

### Post by WannabeFantasma on 2010-05-28
No one? :o

---

### Post by rayclev on 2010-05-28
Sorry. I don't know how in Ubuntu. In other distro's I edit 'menu.list' in /boot/grub.
Cheers. Ray

---

### Post by bcbc on 2010-05-28
Sound like bcdedit as it's the vista menu offering your choice of windows. Search google for that and you'll probably find an answer.

---

### Post by Elfy on 2010-05-28
moved to general help

you could try

```
sudo update-grub
```

---

