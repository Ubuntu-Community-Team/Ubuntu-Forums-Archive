---
title: "Not able to add new programs"
date: 2010-06-03
forum: General Help
---

### Post by nlindz2065 on 2010-06-03
Hello, I am trying to add a program that will allow me to play wmv files on my computer.  I'm not sure what version of Ubuntu I am using but I keep getting a message that says:
E:dpkg was interrupted, you must manually run'dpkg --configure -a'to correct the problem.
E:_cache->open()failed,please report.
When I try to run this in the terminal I get a message saying I need to be a superuser.  Can anyone help me?

---

### Post by Tim Sharitt on 2010-06-03
Run:
```
sudo dpkg --configure -a
```
Then enter your password when prompted.

---

### Post by nlindz2065 on 2010-06-03
Thanks, I think that worked.  I really don't know what I'm doing but your advice helped!

---

### Post by sanderd17 on 2010-06-03
With the sudo command, you temporarily become root. sudo stands for "SUperuser DO ...". As root, you have all rights over the system and you can alter the directories and files you want.

In Linux distros that aren't derived from ubuntu, it's normal to have a separate root account. You have to log out as normal user and log in back as root to install something. Because many newbies would stay logged in as root and this is a security problem, Ubuntu has chosen for a temporarily root in the form of the sudo command.

If you want to learn more about commands, visit the site [http://gd.tuwien.ac.at/linuxcommand.org/]("http://gd.tuwien.ac.at/linuxcommand.org/"), it's where I leared the basics of commandline.

---

