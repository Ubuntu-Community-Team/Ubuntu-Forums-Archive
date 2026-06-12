---
title: "problem with JDK installation"
date: 2010-11-21
forum: General Help
---

### Post by libioz on 2010-11-21
Hello!
I tried to run:
 
[EMAIL="oot@user-Satellite-U500:/home/user"]oot@user-Satellite-U500:/home/user[/EMAIL]# sudo apt-get update install sun-java6-jdk
 
and I have got this:

E: The update command takes no arguments
[EMAIL="root@user-Satellite-U500:/home/user"]root@user-Satellite-U500:/home/user[/EMAIL]# sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'sun-java6-jdk' has no installation candidate
 
What is the problem?
 
I need JDK for Linux 32bit.
Where can I download the package?
Thanks!

---

### Post by wojox on 2010-11-21
Get out of root.

```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"

```

```
sudo apt-get update
```

---

### Post by libioz on 2010-11-21
That is what I did, I think.
I wrote:
[SIZE=3][FONT=Calibri]Sudo add-apt – repository “deb  [/FONT][/SIZE][[FONT=Calibri][SIZE=3]http://archive.canonical.com/[/SIZE][/FONT]]("http://archive.canonical.com/")[SIZE=3][FONT=Calibri] lucid partner”[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Sudo apt-get update[/FONT][/SIZE]
**[FONT=Calibri][SIZE=3]Sudo apt-get install sun-java6-jdk[/SIZE][/FONT]**

---

### Post by libioz on 2010-11-21
[SIZE=3]Sorry[/SIZE]
[SIZE=3]I did not get out of root.[/SIZE]
[SIZE=3]Now it worked![/SIZE]
[SIZE=3]Thank you!
[/SIZE]

---

