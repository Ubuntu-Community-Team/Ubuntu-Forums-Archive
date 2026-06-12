---
title: "Where did apt-get install that package?"
date: 2010-01-10
forum: General Help
---

### Post by eweibust on 2010-01-10
I'm still trying to get comfortable with apt-get doing all my installing for me.  The one question I have now is how do I find out where apt-get install "some_package" puts the package it installed for me?

---

### Post by michy99 on 2010-01-11
It puts different parts of it in different places. If you look at the package in Synaptic Package manager and look at the properties, it will list all the files installed and where they are.

---

### Post by vinnywright on 2010-01-11
well you could find it in synaptic rite click it then click propertys and the instaled files tabe.

or use locate like.

locate somepackage

but it may spit out a fire hose of text iin the terminal so best to pipe it to less or more like

locate somepackage | less

for less
use enter for 1 more line
page-down screen of text at a time 
q to quit

VINNY

---

### Post by ciscosurfer on 2010-01-11
> **eweibust said:**
> I'm still trying to get comfortable with apt-get doing all my installing for me.  The one question I have now is how do I find out where apt-get install "some_package" puts the package it installed for me?You can also use **dpkg** on the command line to tell you where installed packages and their related files have been placed. For example, you can type```
dpkg -L empathy
```and get the following```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/empathy
/usr/share/doc/empathy/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/empathy-logs.1.gz
/usr/share/man/man1/empathy.1.gz
/usr/share/man/man1/empathy-accounts.1.gz
/usr/share/applications
/usr/share/applications/empathy.desktop
/usr/share/dbus-1
/usr/share/dbus-1/services
/usr/share/dbus-1/services/org.freedesktop.Telepathy.Client.Empathy.service
/usr/share/telepathy
/usr/share/telepathy/clients
/usr/share/telepathy/clients/Empathy.client
/usr/share/indicators
/usr/share/indicators/messages
/usr/share/indicators/messages/applications
/usr/share/indicators/messages/applications/empathy
/usr/bin
/usr/bin/empathy
/usr/bin/empathy-logs
/usr/share/doc/empathy/README
/usr/share/doc/empathy/TODO
/usr/share/doc/empathy/AUTHORS
/usr/share/doc/empathy/changelog.gz
/usr/share/doc/empathy/NEWS.gz
/usr/share/doc/empathy/changelog.Debian.gz
```For more on **dpkg** check the man pages```
man dpkg
```

---

### Post by tgalati4 on 2010-01-11
sudo apt-get install htop
which htop
locate htop
apropos htop
htop

---

