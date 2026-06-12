---
title: "Windows Drive in Linux"
date: 2010-10-20
forum: General Help
---

### Post by HpZ on 2010-10-20
Hi, I used Samba to setup a Linux network drive in Windows. Is there anyway to do it vise versa?

A guide of some sorts? I know it includes mounting and stuff.

---

### Post by Ugluk on 2010-10-20
Smbfs appears bugged in Ubuntu, and does not work with Vista/7 fileservers. You can use GFVS to temporarily mount a drive via fuse, which works.

---

### Post by HpZ on 2010-10-20
OK so I set up the Windows Share in my File Browser. But I need to navigate to the share in the temrinal (CLI). Where is it located? I tried:
```
root@enterprise:~# cd smb://fin@bebop/users/fin
bash: cd: smb://fin@bebop/users/fin: No such file or directory

```
I tried
```
root@enterprise:~# smb://fin@bebop/users/fin
bash: smb://fin@bebop/users/fin: No such file or directory

```

What the heck?

---

### Post by srs5694 on 2010-10-21
You should be able to do it using the cifs filesystem type code. [Here](http://www.cyberciti.biz/faq/linux-mount-cifs-windows-share/) is a Web page that describes the basics. It's also possible to create an /etc/fstab entry to do it automatically when you boot. [Here's](http://bobpeers.com/linux/mount) a page that describes this (near the end; search for "cifs").

---

### Post by Schrute Farms on 2010-10-21
This may not be exactly what you're looking for, but I have no problem mounting my wife's work XP computer using the network entry in Nautilus.   I just clicked on network in the left places plane, then on windows network, and so on until I found her computer.  I just entered the windows password and told it to always remember it.  Now it's in my bookmarks, one click and it's mounted.  I don't know the command, but I'm sure it would be very easy to auto-mount.

---

