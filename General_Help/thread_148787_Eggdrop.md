---
title: "Eggdrop"
date: 2006-03-22
forum: General Help
---

### Post by Elen on 2006-03-22
Help please.
I badly speak in English. I from Russia.
Help to establish eggdrop

```
sudo bash *******
apt-get upload
apt-get install eggdrop
```

What is farther?

---

### Post by az on 2006-03-22
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)
Or the corresponding page on
[http://ubuntu-ru.org/Wiki/](http://ubuntu-ru.org/Wiki/)

Enable the universe repository and then run

sudo apt-get update
sudo apt-get install eggdrop.
------

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) &#1048;&#1083;&#1080; &#1089;&#1086;&#1086;&#1090;&#1074;&#1077;&#1090;&#1089;&#1090;&#1074;&#1091;&#1103; &#1089;&#1090;&#1088;&#1072;&#1085;&#1080;&#1094;&#1072; &#1085;&#1072; [http://ubuntu-ru.org/Wiki/](http://ubuntu-ru.org/Wiki/) 

&#1042;&#1082;&#1083;&#1102;&#1095;&#1080;&#1090;&#1077; &#1072;&#1088;&#1093;&#1080;&#1074; &#1074;&#1089;&#1077;&#1083;&#1077;&#1085;&#1085;&#1086;&#1075;&#1086; &#1080; &#1087;&#1086;&#1089;&#1083;&#1077; &#1101;&#1090;&#1086;&#1075;&#1086; &#1087;&#1086;&#1073;&#1077;&#1075;&#1080;&#1090;&#1077; 


sudo apt-get update
sudo apt-get install eggdrop

---

### Post by r4ik on 2006-03-22
Just when i thought i have seen almost everything on this Forum :)

---

### Post by az on 2006-03-22
Bored2k is studying, like, five languages.  He doesn't need to use babelfish like I do....

---

### Post by Elen on 2006-03-24
```
<renat> Eggdrop v1.6.17 (C) 1997 Robey Pointer (C) 2004 Eggheads
<renat> [17:39] --- Loading eggdrop v1.6.17 (Fri Mar 24 2006)
<renat> [17:39] Listening at telnet port 7510 (all).
<renat> [17:39] Can't load modules dns: /usr/bin/modules/dns.so: cannot open shared object file: No such file or directory
<renat> [17:39] Can't load modules channels: /usr/bin/modules/channels.so: cannot open shared object file: No such file or directory
<renat> [17:39] Can't load modules server: /usr/bin/modules/server.so: cannot open shared object file: No such file or directory
<renat> [17:39] Can't load modules ctcp: /usr/bin/modules/ctcp.so: cannot open shared object file: No such file or directory
<renat> [17:39] Can't load modules irc: /usr/bin/modules/irc.so: cannot open shared object file: No such file or directory
<renat> [17:39] Can't load modules notes: /usr/bin/modules/notes.so: cannot open shared object file: No such file or directory
<renat> [17:39] Can't load modules console: /usr/bin/modules/console.so: cannot open shared object file: No such file or directory
<renat> [17:39] Can't load modules uptime: /usr/bin/modules/uptime.so: cannot open shared object file: No such file or directory
```

What to do?
Help please.

---

### Post by frodon on 2006-03-24
Launch your eggdrop from the /usr/lib/eggdrop directory : ```
cd /usr/lib/eggdrop
eggdrop -m path_to_config_file 
```(use the -m tag only the first time you launch the eggdrop as to create the user files)

---

