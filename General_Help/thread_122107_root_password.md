---
title: "root password"
date: 2006-01-26
forum: General Help
---

### Post by Thulemanden on 2006-01-26
For some reason I seem not to have a password, or the right one, for the superuser but the system asks for one for installing software. What do I do? is there a standard initial password?

---

### Post by kaamos on 2006-01-26
You normally should use sudo insead of su. You can login as root with "sudo su" though. More info -> [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by HenryTheGreat on 2006-01-26
Or just type in (I think) 

su passwd root

And then input a password.

---

### Post by Tichondrius on 2006-01-26
ROFL at two wrong posts above:

To change the root password you need to do "sudo -s" to get a root shell and then type "passwd" to set the new password, and exit the shell.

Alternatively you can just do "sudo passwd" but that is a little confusing because you need to first type your own password followed by the new root password twice.

---

### Post by Thulemanden on 2006-01-26
Thanks; I used 

sudo su
the password

I had kubuntu installed some time ago; and now I recall it.

---

### Post by Sutekh on 2006-01-26
Besides which, you don't really want to use root.  You should be able to install software and do everything you need using sudo.  Less chance of mesing things up. 

The sudo passord should be the password for your user.

---

### Post by Thulemanden on 2006-01-26
All right; I'll make a note of that.

---

### Post by aysiu on 2006-01-26
[QUOTE=Sutekh]Besides which, you don't really want to use root.  You should be able to install software and do everything you need using sudo.  Less chance of mesing things up.[/QUOTE] See the third link of my signature for more details.

---

### Post by Thulemanden on 2006-01-26
Aysiu, you wouldn't know if I can edit the menu in gedit? If so, where would the file be?

I am using Hoary Hedgehog until I receive the new updated CD's.

---

### Post by aysiu on 2006-01-26
[QUOTE=Thulemanden]Aysiu, you wouldn't know if I can edit the menu in gedit? If so, where would the file be?

I am using Hoary Hedgehog until I receive the new updated CD's.[/QUOTE] The applications menu?

---

