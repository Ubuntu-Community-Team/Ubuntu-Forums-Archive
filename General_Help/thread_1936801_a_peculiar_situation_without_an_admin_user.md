---
title: "a peculiar situation without an admin user"
date: 2012-03-06
forum: General Help
---

### Post by mustafi05 on 2012-03-06
I am using ubuntu11.10 64 bit version . while checking the user account i have changed my admin user as an standard user. As aresult there is no more admin user. and here the problem begins . whereever authentication is needed it is asking for admin password . the former admin password is not working , as it has became a standard users password .I am unable to make that account an admin one as this also recquire an admin password. As a result i can not install any app from ubuntu software centre or even can not download security update. what should i do? please suggest me.

---

### Post by Diametric on 2012-03-06
If it is your machine, you can boot into recovery mode which will give you the ability to reset the user account as the shell you get is a root shell.

---

### Post by miegiel on 2012-03-06
Edit /etc/sudoers so you can sudo and gksudo things again.

```
nano /etc/sudoers
```
under the line
```
root	ALL=(ALL:ALL) ALL
```
add this line
```
your-user-name	ALL=(ALL:ALL) ALL
```
With your own username instead of *"your-user-name"* ;)

Assuming you do it from the recovery root shell. You can also do it booting from a ubuntu liveCD (or even by sticking your disk in another linux machine), but you'll need to make sure that you edit the right *sudoers* file then. Probably something like */media/disk/etc/sudoers*.

---

### Post by mustafi05 on 2012-03-11
thank you miegiel . i have tried what you have said . when i boot in recovery mode and and typed /etc/sudoers it replies permission denied. have i done the right,  or you say to do any thing else? thanks again.

---

### Post by Cheesemill on 2012-03-11
> **miegiel said:**
> Edit /etc/sudoers so you can sudo and gksudo things again.

```
nano /etc/sudoers
```

Don't do this unless you want to risk more breakage. Instead use:
```
visudo
```visudo is a program that opens the sudoers file with an editor and then checks that the syntax of the file is correct before saving it. If you make a typo in your sudoers file it will be more things to fix. If you're uncomfortable using vi then you can use nano instead by doing:
```
EDITOR="nano" visudo
```[SIZE=3]***BUT***[/SIZE]
There is no need to do any of the above at all. You are going to have to use recovery mode anyway so you may as well just do:
```
gpasswd -a <user> admin
```Replacing <user> with your username to add yourself back to the Administrators group.

---

