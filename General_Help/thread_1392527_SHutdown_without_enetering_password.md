---
title: "SHutdown without enetering password"
date: 2010-01-28
forum: General Help
---

### Post by gunjannigam on 2010-01-28
I want to close my system using a scipt. The scipt runs shutdown -h now to close the system but it needs root privileges. I dont want to enter the password every time on terminal. Is there a way that the commnad can be run with root privilege or the password could be saved in some file or in the scipt itself so that it does not asks for password each time I run the scipt. Please help

---

### Post by realzippy on 2010-01-28
```
[B]sudo chmod +s /sbin/shutdown 
[/B]
```
gives superuser flag to shutdown

---

### Post by sisco311 on 2010-01-28
> **gunjannigam said:**
> I want to close my system using a scipt. The scipt runs shutdown -h now to close the system but it needs root privileges. I dont want to enter the password every time on terminal. Is there a way that the commnad can be run with root privilege or the password could be saved in some file or in the scipt itself so that it does not asks for password each time I run the scipt. Please help

Edit the sudoers file:
```
sudo visudo
```
and append it with:
```
**username** ALL=(root) NOPASSWD:/sbin/shutdown -h now
```
replace **usernaem** with your login name.

[thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by gunjannigam on 2010-01-28
> **realzippy said:**
> [B]sudo chmod +s /sbin/shutdown 
[/B]
gives superuser flag to shutdown
It still asks for password

---

### Post by realzippy on 2010-01-28
> **gunjannigam said:**
> It still asks for password

???
Do you still run "sudo" ?
Try:

**shutdown -h now**

---

### Post by gunjannigam on 2010-01-28
> **realzippy said:**
> ???
Do you still run "sudo" ?
Try:

**shutdown -h now**
Yaa I still use sudo
Without sudo it says you need to be root

---

### Post by gunjannigam on 2010-01-28
sisco311 method worked thanks

---

### Post by realzippy on 2010-01-28
*Without sudo it says you need to be root*

yep,until you run:sudo chmod +s /sbin/shutdown,then it will not ask  ;-)

but anyway sisco311's method is smarter.. at least on multiuser systems ...

---

