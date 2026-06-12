---
title: "User not in the sudoers file"
date: 2011-07-15
forum: General Help
---

### Post by koszta on 2011-07-15
Hi,

I have a bit of a problem... I thought (for certain reasons) I would just add myself to root group and therefore gain some more rights for my account. I could sudo before... But once I gained the root group as a secondary group it says I am not in the sudoers file anymore... 

```
id 
uid=1000(kosta) gid=1000(kosta) groups=0(root),1000(kosta)

```

```
sudo ls
[sudo] password for kosta: 
kosta is not in the sudoers file.  This incident will be reported.

```

It is really weird and messed up. I can view sudoers file but not edit it... I can cat passwd but I can not view syslog... 
Is there any way to fix this without having to reboot to recovery mode?  And why the heck is this happening after all?

thanks

---

### Post by nothingspecial on 2011-07-15
Sounds to me like you did usermod without the -a (usermod -G root)

See my sig

To get yourself out of it, you have to boot into recovery mode and type
```

usermod -a -G admin [COLOR="Red"]username[/COLOR]
```

Where the red username is your real username.

---

### Post by koszta on 2011-07-16
Yep, thats what I did.. What an idiot am I :D ...

I am just too much user to RHEL and root. So I assume that every user allowed to do sudo on Ubuntu is a member of admin group , right?

---

