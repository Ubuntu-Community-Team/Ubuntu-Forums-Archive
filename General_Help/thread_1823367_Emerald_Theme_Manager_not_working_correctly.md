---
title: "Emerald Theme Manager not working correctly"
date: 2011-08-12
forum: General Help
---

### Post by linuxuser12345 on 2011-08-12
Every time I choose a theme in this thing, the system never switches over to it. Am I supposed to log out, then log back in again to enable the newly installed .emerald themes? I tried running "emerald --replace", but my system just screws up once I do that: The window decorations completely remove themselves and I am stuck with uncontrollable windows.
I am using Ubuntu 11.04 in Classic mode. Can anyone help me?

---

### Post by bestemdaanhel on 2011-08-12
> **linuxuser12345 said:**
> Every time I choose a theme in this thing, the system never switches over to it. Am I supposed to log out, then log back in again to enable the newly installed .emerald themes? I tried running "emerald --replace", but my system just screws up once I do that: The window decorations completely remove themselves and I am stuck with uncontrollable windows.
I am using Ubuntu 11.04 in Classic mode. Can anyone help me?

I have the same issue as well. I've tried running in Ubuntu, Ubuntu Classic, Unity 2d.. None of them switch themes with Emerald and I have the window decorations plugin enabled in Compiz with ccsm.

---

### Post by bestemdaanhel on 2011-08-12
```
sudo apt-get purge emerald

sudo apt-get install libwnck-dev libwnck1.0-cil-dev git automake libtool intltool libdecoration0 libdecoration0-dev

sudo apt-get install git

git clone git://anongit.compiz.org/fusion/decorators/emerald

cd emerald

git checkout -b compiz++ origin/compiz++

./autogen.sh

./configure --prefix=/usr/local

make && sudo make install

emerald --replace
```

You may need to reinstall the Emerald Theme Manager from the Ubuntu Software Center.

---

### Post by linuxuser12345 on 2011-08-12
It worked! Thank you! :)

---

### Post by linuxuser12345 on 2011-08-12
Okay, now Emerald won't activate until I go into a terminal and type in "emerald --replace". And after I type that in, if I close the terminal the window decorations disappear again. I already have "emerald --replace" typed in on my startup applications menu, but Emerald still simply doesn't load at startup. :(

---

### Post by bestemdaanhel on 2011-08-12
System-> Preferences -> Startup Applications or search for Startup Applications. Once there add the following to have Emerald run at login:

```
Name: Emerald Theme Manager
Command: emerald --replace
Comment: Emerald
```

---

### Post by linuxuser12345 on 2011-08-12
It started working. Thank you :)

---

