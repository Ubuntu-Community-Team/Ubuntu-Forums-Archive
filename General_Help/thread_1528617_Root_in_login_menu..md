---
title: "Root in login menu."
date: 2010-07-11
forum: General Help
---

### Post by redcodefinal on 2010-07-11
Hi,
I am running Ubuntu Pentest Edition and I would like to know how to have the root account show up on my login screen. I can already log in to it as i changed the password. I need to do this because I am sick of having to type in sudo before every command I wirte and it would just be simpler to log in as root.

---

### Post by lisati on 2010-07-11
We don't usually allow "login as root" tutorials.
Please have a read here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bodhi.zazen on 2010-07-11
As indicated by [[COLOR=#D40000]**lisati**[/COLOR]]("http://ubuntuforums.org/member.php?u=327635")  , we do not support logging into a graphical session as root for daily use.

There are rare times when it may be necessary, and in that case it would be supported.

I suggest you use sudo

```
sudo -i
```gives a root shell.

For graphical application, use gksu

```
gksu nautilus
```

Best of luck to you.

---

