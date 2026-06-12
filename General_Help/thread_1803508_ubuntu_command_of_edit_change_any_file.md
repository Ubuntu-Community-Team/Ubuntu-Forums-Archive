---
title: "ubuntu command of edit /change any file"
date: 2011-07-13
forum: General Help
---

### Post by hubsatconet on 2011-07-13
USER="ntop"
INTERFACES="eth1"   


-how to edit the above file from eth1 to eth0 on command

---

### Post by dino99 on 2011-07-13
select network settings icon

---

### Post by seawolf167 on 2011-07-13
If you know the file you want to edit, you can open it in any editor, i.e.

```
gedit /path/to/filename
```or in your example, you probably want

```
sudo gedit /etc/network/interfaces
```its always a good idea to make a backup before you edit any configuration file

```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```or easier

```
cp filename{,.bak}
```

---

