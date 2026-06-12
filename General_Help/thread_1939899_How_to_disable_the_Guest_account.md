---
title: "How to disable the Guest account"
date: 2012-03-12
forum: General Help
---

### Post by geek2330 on 2012-03-12
I followed some instructions and opened the file  /etc/lightdm/lightdm.conf

Added the line
allow-guest=false

When saving the document it tells me I dont have permissions. I am an Admin on this Ubuntu 11.10

Dod I need to open terminal and execute any sudo command, which?

---

### Post by sudodus on 2012-03-12
> **geek2330 said:**
> I followed some instructions and opened the file  /etc/lightdm/lightdm.conf

Added the line
allow-guest:false

When saving the document it tells me I dont have permissions. I am an Admin on this Ubuntu 11.10

Dod I need to open terminal and execute any sudo command, which?
Try editing as root with nano
```
sudo nano /etc/lightdm/lightdm.conf
```

---

### Post by geek2330 on 2012-03-12
Thanks, that did the trick...!!

---

### Post by sudodus on 2012-03-13
> **geek2330 said:**
> Thanks, that did the trick...!!
You are welcome :KS
Please click [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page and select 'Mark the this thread as SOLVED'

---

