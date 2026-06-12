---
title: "KDM problems"
date: 2006-03-08
forum: General Help
---

### Post by boichukj on 2006-03-08
Hi
Im having a problem that kdm is loading then taking me back to the console.  When linux is loading it loads kdm then sends me to the console.  Ive tried doing a kdm stop kdm start but it still boots me back.  

Any suggestions?

---

### Post by aysiu on 2006-03-08
Do you get any errors?

---

### Post by boichukj on 2006-03-08
OK i did a kdm stop then i tried startx and it gave me errors with my nvidia setup.  

I followed the binary install for them.  Guess it didnt work.  I tried the manual install and it gave me errors.  Said there was a problem with the make file.

---

### Post by incubus on 2006-03-09
So everything was working before?

Anything unusual in your
/var/log/Xorg.0.log ?

Do you know where the binaries are failing?

incubus

---

### Post by boichukj on 2006-03-09
Its weird.  It works fine in Ubuntu but for some reson I cant get it to work in Kubuntu.  Whats so different between the two that could cause this problem?

I think I i will just reinstall Ubuntu.  Is there a way to install KDE while using Ubuntu?

---

### Post by incubus on 2006-03-09
X doesn't start even if you replace your driver for "vesa"?

But well, yes, you can definitely do:
$ sudo apt-get install kdebase

while in Gnome. From there you can install the other kde packages you want.

incubus

---

