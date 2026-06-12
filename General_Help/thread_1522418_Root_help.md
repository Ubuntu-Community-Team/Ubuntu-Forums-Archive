---
title: "Root help"
date: 2010-07-02
forum: General Help
---

### Post by artyjaimes on 2010-07-02
Hello guys, I am not new to ubuntu but i am also not an expert. I recently installed ubuntu 10 and so far it is great. 

The thing is when installing it did not ask me for a root password. Now when i am trying out certain commands it asks me for a root password. Since i didnt create one it keeps saying authentication failure. I am only using the user i created when installing. How do i create a root password or root user on ubuntu 10? 
 
I apologize if this has been asked already. Thanks in advance.

---

### Post by yetiman64 on 2010-07-02
If you are the only user on the system, you will be in the sudoers file, thus the "root" password being asked for **is your user account password** you use to log in. Use it any time you're asked for the root password.

Edit : A good idea is to have a read of link #4 in my sig. (Following from the link)
re. root password
> **By default, the root account password is locked in Ubuntu.**  This means that you cannot login as root directly or use the su  command to become the root user.and
>  Just remember, when sudo asks for a password, it needs **YOUR  USER password**, and not the root account password. Setting a root password is possible to do, **but is seriously not recommended.**

> To enable the root account (i.e. set a password) use:  Note: [U][I]**I'm deliberately leaving out the command (yetiman64).**
[/I][/U]and> **Use at your own risk! **Please read the [RootSudo]("https://help.ubuntu.com/community/RootSudo") documentation carefully before following any commands to enable the root account in Ubuntu, it is a very good way to compromise or destroy your system.

---

### Post by burton247 on 2010-07-02
and to set a root password

```

sudo passwd

```

You'll need your user password again though

---

### Post by Rubi1200 on 2010-07-02
This will also provide information about authentication on Ubuntu:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Just be very careful if you decide to try and change anything (which I recommend you do not).

Ubuntu is a powerful and secure OS with its default settings.

---

### Post by philinux on 2010-07-02
See this for security in Ubuntu.
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

**And this for forum policy.**
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by artyjaimes on 2010-07-02
Thank you very much guys, you answered fast and very helpful. Yeah i know it is not a good idea to mess with root, but the thing is i started taking a linux class. So i dont mind if i mess things up. --thanks again.

---

