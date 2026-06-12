---
title: "Getting a clean reinstall through apt-get"
date: 2010-08-11
forum: General Help
---

### Post by kingkrakauer on 2010-08-11
Hey, I'm trying to get Samba running, but I accidentally deleted smb.conf. I tried reinstalling Samba through apt-get, but it does not create another smb.conf (which it did when I first installed it). I'm pretty new to ubuntu, and I'm just wondering if anybody knows how to get a completely clean install. Thanks!

---

### Post by kerry_s on 2010-08-11
competly remove it then reinstall. use synaptic package manager to install/remove/upgrade you can see whats going on better, on the bottom left click status.

---

### Post by cavalier911 on 2010-08-12
```
sudo find / -iname smb.conf
/usr/share/samba/smb.conf
/etc/samba/smb.conf

```If I delete the copy in /etc/samba::(

```
sudo cp /usr/share/samba/smb.conf /etc/samba
```The lesson of the day is use nano with -B option:
```
sudo nano **-B** /etc/samba/smb.conf
```Automatically backs up the previous version adding a ~ to the end of the file name.

So if you delete or incorrectly edit the file you have a backup to restore.;)

---

