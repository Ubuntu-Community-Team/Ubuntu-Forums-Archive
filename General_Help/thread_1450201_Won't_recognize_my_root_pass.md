---
title: "Won't recognize my root pass?"
date: 2010-04-08
forum: General Help
---

### Post by Doddow on 2010-04-08
Su <pass here> then enter

I get; 
su: Authentication failure

It's not the wrong pass, i even changed it.
Help me please. :(

---

### Post by lisati on 2010-04-08
The preferred method of elevevating user privileges in Ubuntu is with the "sudo" command. Have a look here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by sisco311 on 2010-04-08
The root account password, by default, is locked, use sudo:
[uhelp]community/RootSudo[/uhelp]

---

### Post by Doddow on 2010-04-08
> **sisco311 said:**
> The root account password, by default, is locked, use sudo:
[uhelp]community/RootSudo[/uhelp]

darwin@ubuntu:~$ sudo pass root
[sudo] password for darwin: 
sudo: pass: command not found

why?

---

### Post by Ahadiel on 2010-04-08
> **Doddow said:**
> darwin@ubuntu:~$ sudo pass root
[sudo] password for darwin: 
sudo: pass: command not found

why?

[https://help.ubuntu.com/community/RootSudo#Enabling the root account](https://help.ubuntu.com/community/RootSudo#Enabling the root account)

That should be **passwd** not **pass**.

---

### Post by sisco311 on 2010-04-08
> **Doddow said:**
> darwin@ubuntu:~$ sudo pass root
[sudo] password for darwin: 
sudo: pass: command not found

why?

Before you try to set up a root password, please read the link from my first post & this one:  [thread=716201]Forum policy on log-in-as-root tutorials[/thread]

---

### Post by lisati on 2010-04-08
Hmmmm.... Are you by any chance trying to set your root password by any chance? You don't normally need to, and can do pretty much all you need to that requires root privileges by prepending "sudo" to the administrative command.

---

### Post by skao on 2010-04-08
Hi Doddow

I think you need to use sudo instead of su

i.e. sudo chmod 777 myfile.sh

when ask for password put in your "administrator user" password, normally this is the password of the first user account you created when you install your Ubuntu.

hope this help

Regards,
Stephen

---

### Post by skao on 2010-04-08
Hi Doddow

*Do not* try to change your "root" password ever.

I tried once when I start using Ubuntu 7.04. From memory it break the whole system.

So just use sudo as everyone suggested. 

Regards,
Stephen

---

### Post by Doddow on 2010-04-08
Thanks alot guys, it got solved.

/Thread

---

### Post by lisati on 2010-04-08
Thread closed at OP's request. Don't forget to mark it as "solved" using the "thread tools" at the top of the page.

---

