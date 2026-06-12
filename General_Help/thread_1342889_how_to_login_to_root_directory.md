---
title: "how to login to root directory"
date: 2009-12-01
forum: General Help
---

### Post by ishfady on 2009-12-01
Hi

I have installed ubuntu 9.10.
How do I log into root folder.

What is the user name and password.
Please can someone guide me.

many thank

---

### Post by trytenn on 2009-12-01
Hi!
What do u want to do? Do u want to log in to your computer as root? That is not a good solution, it's a loot of security risks with it. The best thing to do is to run the sudo command in a terminal. See in the main menu > Accessories> Terminal.
U type in sudo and the command/program u want to run as root. And u will be prompted for password.
Please describe more precis what u want to do, maybe I can help.

//Simon

---

### Post by HiImTye on 2009-12-01
you can sudo any command you want to do. this will cause the terminal to ask you for *your* password (assuming that you have administrative rights - if youre the only user then you should). to do this then you would enter the command as such
```
sudo <command>
```
and if it is a graphical program then you would use
```
gksudo <command>
```
if you want a persistent root shell then you can use one of the following:
```
sudo -i
```
```
sudo su
```
the second one will start you in the location your shell is currently in

for more info see
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by syberhunter on 2009-12-06
Ok, so what if i'm trying to install something like the Ubuntulooks GTk engine, and the instructions say to copy some lib files into a folder as 'root' what then?

---

### Post by SuperSonic4 on 2009-12-06
You'll have to be in the directory where the extracted tarball is

Use sudo together with cp

```
sudo cp -v 'libubuntulooks.so' 'libubuntulooks.la' /usr/lib/gtk-2.0/2.*.*/engines
```

```
cp -Rv Human /usr/share/themes/ 
```

---

### Post by syberhunter on 2009-12-06
> **SuperSonic4 said:**
> You'll have to be in the directory where the extracted tarball is

Use sudo together with cp

```
sudo cp -v 'libubuntulooks.so' 'libubuntulooks.la' /usr/lib/gtk-2.0/2.*.*/engines
``````
cp -Rv Human /usr/share/themes/ 
```

ok, i'm in the directory where i extracted the tarball, copied the command you wrote and pasted it into the terminal and i get
cp: cannot stat `libubuntulooks.so': No such file or directory
cp: cannot stat `libubuntulooks.la': No such file or directory

---

