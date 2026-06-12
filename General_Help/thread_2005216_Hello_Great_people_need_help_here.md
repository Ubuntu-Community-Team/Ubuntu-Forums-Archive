---
title: "Hello Great people need help here"
date: 2012-06-17
forum: General Help
---

### Post by sparko0317 on 2012-06-17
I have installed Ubuntu 12.04 on my computer alongside with windows 7 using wubi installer , and after a months of using ubuntu i've decided to say goodbye to windows . How to remove windows 7 completely while keeping my current Ubuntu installs , settings, and all those softwares that i downloaded from ubuntu site ?

---

### Post by codemaniac on 2012-06-17
As you have mentioned it is not a normal Ubuntu install(wubi) , my bet would to backing up all the data you have and do a clean Ubuntu install .

---

### Post by kc1di on 2012-06-17
> **sparko0317 said:**
> [FONT="Trebuchet MS"][SIZE="3"]I have installed Ubuntu 12.04 on my computer alongside with windows 7 using wubi installer , and after a months of using ubuntu i've decided to say goodbye to windows . How to remove windows 7 completely while keeping my current Ubuntu installs , settings, and all those softwares that i downloaded from ubuntu site ?[/SIZE][/FONT]
I don't believe that it would be possible to remove windows and keep a WUBI install because in a WUBI install Ubuntu is installed in a Windows Folder which would be deleted when you remove windows.

Best bet would be to to a complete reinstall of Ubuntu and back up all your data and reload it on the new install.

---

### Post by wilee-nilee on 2012-06-17
Here is a link for moving the wubi to a partition.
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)

---

### Post by hakermania on 2012-06-17
> **wilee-nilee said:**
> Here is a link for moving the wubi to a partition.
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
Nice link! I wasn't aware that something like this is possible!

*PS*
Not sure if:
"Hello Great people, (I) need help here"
or:
"Hello, Great people need help here"
:lol:

---

### Post by zombifier25 on 2012-06-17
> **hakermania said:**
> *PS*
Not sure if:
"Hello Great people, (I) need help here"
or:
"Hello, Great people need help here"
:lol:

lool

To OP: Don't run the script provided by the link just yet. You need to partition the drives first. Boot off a LiveCD/USB, give Ubuntu an ext4 partition using GParted. If you don't know how, better take a screenshot of GParted and post it here.

---

### Post by wilee-nilee on 2012-06-17
> **zombifier25 said:**
> lool

To OP: Don't run the script provided by the link just yet. You need to partition the drives first. Boot off a LiveCD/USB, give Ubuntu an ext4 partition using GParted. If you don't know how, better take a screenshot of GParted and post it here.
First sentence in the wiki.
**This document describes how to migrate a Wubi install to partition. The partition(s) must be created already.**

---

