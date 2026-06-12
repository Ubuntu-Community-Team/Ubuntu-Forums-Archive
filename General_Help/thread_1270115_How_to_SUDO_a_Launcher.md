---
title: "How to SUDO a Launcher"
date: 2009-09-19
forum: General Help
---

### Post by yogiman.uk on 2009-09-19
Hi

I have a couple of applications that require running as SUDO.  I don't want to drop to a terminal and type a command to run an application so is it possible to create a launcher that runs a program and includes the SUDO and password credentials.

for example:-

At the moment I have to drop to a terminal and type:-

sudo netExtenderGui
Enter the password

This is very long winded and I would like to just click a desktop launcher.

You used to be able to do this for example sudo nautilus but no longer.

Any help you can off would be great.

Thanks in advance.

Yogiman!

---

### Post by NoaHall on 2009-09-19
"gksudo nautilus" as a command in a launcher.

---

### Post by scragar on 2009-09-19
You can edit the suders file to remove the password for single applications.

[http://www.gratisoft.us/sudo/man/sudoers.html](http://www.gratisoft.us/sudo/man/sudoers.html) (More comprehensive)

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers) (Easier to understand)

For simplicity:
```
sudo su
gedit /etc/sudoers
```
Add these lines to the end:
```
Cmnd_Alias EVIL_CMDS = /usr/bin/nautilus, /usr/bin/application2
ALL ALL=(ALL) NOPASSWD: EVIL_CMDS
```

---

### Post by VCoolio on 2009-09-19
It is recommended to use gksudo for graphical applications. [Read here why]("http://www.psychocats.net/ubuntu/graphicalsudo"). Convenient for launchers, but also if you run them from the terminal you better use that.

---

### Post by yogiman.uk on 2009-09-19
Wow you guys are really awesome, I love Ubuntu for just this reason, kind, helpful, intelligent people who put themselves out to help others.

Wicked.. Thank you all very much!

Yogiman!

---

