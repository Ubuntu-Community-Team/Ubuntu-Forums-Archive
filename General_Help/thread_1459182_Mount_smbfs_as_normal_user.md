---
title: "Mount smbfs as normal user"
date: 2010-04-21
forum: General Help
---

### Post by dragos2 on 2010-04-21
I have a mount like this:
```

smbmount //samba/samba /home/user/samba -o username=dragos,password=pass,uid=201,gid=200

```

But I want to add this to .bashrc or /.profile for users who will have this mount in their home.

How can I enable them the right to use this mount ?

---

### Post by vanadium on 2010-04-21
By adding the option "users" to the line in /etc/fstab.

---

### Post by dragos2 on 2010-04-21
> **vanadium said:**
> By adding the option "users" to the line in /etc/fstab.

Can you give me an example please ?

---

### Post by ad_267 on 2010-04-21
Or use mount.cifs

It should have the suid set to root by default in Ubuntu.

```
mount.cifs //samba/samba /home/user/samba -o username=dragos,password=pass,uid=201,gid=200
```

If that doesn't work,
```
sudo chmod a+s /sbin/mount.cifs
sudo chmod a+s /sbin/umount.cifs
```

---

### Post by dragos2 on 2010-04-21
> **ad_267 said:**
> Or use mount.cifs

It should have the suid set to root by default in Ubuntu.

```
mount.cifs //samba/samba /home/user/samba -o username=dragos,password=pass,uid=201,gid=200
```If that doesn't work,
```
sudo chmod a+s /sbin/mount.cifs
sudo chmod a+s /sbin/umount.cifs
```

Great, this works.

Where should I place this to be mounted when a user logs in and unmounted when he logs off ?
Since I don't want to use fstab.

---

### Post by ad_267 on 2010-04-21
Getting it to run on startup is pretty easy, just add the command in System - Preferences - Startup Applications.

The last post on this thread tells you how to run a script on logout [http://ubuntuforums.org/showthread.php?t=252935](http://ubuntuforums.org/showthread.php?t=252935)

Just add this to /etc/gdm/PostSession/Default
```
logoutscript="$HOME/.gdmlogout";
if [ -x "$logoutscript" ] ; then
  su $USER -c "$logoutscript"
fi
```

Then write your logout commands in ~/.gdmlogout.

---

### Post by vanadium on 2010-04-21
The option using fstab would have been to add "users" a line such as:

```

//samba/samba /home/user/samba cifs username=dragos,password=pass,uid=201,gid=200,users,noauto 0 0

```

The "noauto" option makes sure the drive is not mounted at startup. The "users" option assures that any user can mount the share with

```

mount /home/user/samba

```

There is also the "user" option: any user can mount, but only the user that mounted can unmount again.

Use whatever approach suits you best.

---

