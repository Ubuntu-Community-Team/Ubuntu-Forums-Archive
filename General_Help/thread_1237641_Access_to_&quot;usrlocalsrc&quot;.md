---
title: "Access to &quot;/usr/local/src&quot; ?"
date: 2009-08-11
forum: General Help
---

### Post by MacGoose on 2009-08-11
Hi!

I'm a Linux noob.  But I'm also a Windows programmer so I know a bit about architectures and are a fast learner.  So I'm trying to download LAMP as I understand it's called.  Anyway, I'm following a tutorial on how to do it.  And it says to download all the packages to "/usr/local/src" but I seem to have no access to that directory.

I'm on a fresh Ubuntu 9.04 desktop installation and it looks like I'm being treated as the administrator as my password actually works when it asks for permissions to do stuff.

I even tried putting me into the root group but it didn't work either.

So what do I do?

---

### Post by drs305 on 2009-08-11
To access the system folders you have to run things with root privileges. So if copying or doing other tasks via terminal commands, preceed the commands with "sudo". For commands which will open a graphical app such as nautilus, use "gksudo".

Here's a guide on Permissions:
[https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

and another on root sudo:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

A bit of background:  "usr" isn't short for "user", it is for "unix system resources".

---

### Post by oomar on 2009-08-11
ok I think you would be much better off going to System> Administration > Synaptic

and just installing apache2 and php. LAMP is just Linux, you have ubuntu, Apache, youll be getting it through synaptic, MySQL, which i THINK comes with apache, and php and python which you can install php in synaptic and python comes installed. you dont need to install it manually.

---

### Post by mcduck on 2009-08-11
> **MacGoose said:**
> Hi!

I'm a Linux noob.  But I'm also a Windows programmer so I know a bit about architectures and are a fast learner.  So I'm trying to download LAMP as I understand it's called.  Anyway, I'm following a tutorial on how to do it.  And it says to download all the packages to "/usr/local/src" but I seem to have no access to that directory.

I'm on a fresh Ubuntu 9.04 desktop installation and it looks like I'm being treated as the administrator as my password actually works when it asks for permissions to do stuff.

I even tried putting me into the root group but it didn't work either.

So what do I do?

Sounds like you are following overly complicated guide to do this.

The whole LAMP stack can be downloaded & installed automatically with a single command:

```
sudo tasksel install lamp-server
```

(or open Synaptic Package Manager, go to Edit->Mark Packages by Task, select "LAMP server" and then "Apply")

edit: What comes to permissions in Ubuntu, being the first user created on that system you are member of the admin group, which means that you are allowed to do administrative tasks but you are not running with full root privileges all the time, only when you ask for them (+ confirm with your password). And that's done by using "sudo": [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by MacGoose on 2009-08-11
Man that was easy!

Thanx guys!

---

### Post by MacGoose on 2009-08-11
Hi again!

So I installed the LAMP server package.  It seemed to go very well. But I cannot find for example Apache anywhere.

Shouldn't there now be a /usr/local/apache2/ directory?

---

### Post by mcduck on 2009-08-12
> **MacGoose said:**
> Hi again!

So I installed the LAMP server package.  It seemed to go very well. But I cannot find for example Apache anywhere.

Shouldn't there now be a /usr/local/apache2/ directory?
You'll find Apache's configuration files in /etc/apache2, and the WWW root directory (where you put your web pages by default) is /var/www.

(/usr/local is typically used for locally installed stuff, programs that you install from outside of normal software sources.)

This guide should provide some help with using Apache in Ubuntu: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Note that /var/www is owned by root so you won't be able to just drop stuff there as normal user. The easy workaround is to run "gksuod nautilus" to open the file manager as root. I recommend reading the "Virtual Hosts"-section of the above linked document, it will help you creating a new site in your home directory, which is a nice setup if the server is for local development and learning purposes.

---

