---
title: "New lucid system supeuser fails"
date: 2010-07-22
forum: General Help
---

### Post by ivanhoe75 on 2010-07-22
I've installed lucid, enabled superuser, but still can not edit system files I want to reconfigure. I ve tried to make root from users-n-groups, gave most rights - the same fail

---

### Post by marshmallow1304 on 2010-07-22
Are you using sudo?

[Sudo documentation]("https://wiki.ubuntu.com/RootSudo")

---

### Post by lisati on 2010-07-22
As marshmallow1304 has suggested, check out "[sudo]("https://help.ubuntu.com/community/RootSudo")."

"Log in as root/super user" tutorials are discouraged, see [here]("http://ubuntuforums.org/showthread.php?t=1486138").

---

### Post by ivanhoe75 on 2010-07-22
sudo does not work to edit system files.
I make superuser by 'sudo passwd root'
and command su must grant all rights but root rights are unaccessible

---

### Post by nothingspecial on 2010-07-22
> **ivanhoe75 said:**
> sudo does not work to edit system files.

Yes it does - unless you`ve messed about with /etc/sudoers
> **ivanhoe75 said:**
> I make superuser by 'sudo passwd root'
and command su must grant all rights but root rights are unaccessible

Can`t help you with this one, read this
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

What have you done?

---

### Post by ivanhoe75 on 2010-07-22
> **nothingspecial said:**
> Yes it does - unless you`ve messed about with /etc/sudoers


Can`t help you with this one, read this
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

What have you done?

But I can not change anything in /etc/sudoers, am I?
It is like to be closed in closet having key to inserted outside of it

I presume lucid is utterly notadjustable system

---

### Post by nothingspecial on 2010-07-22
You can do whatever you like to lucid - hence sudo ;)

You have to use visudo

```
sudo visudo
```

Read this

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by ivanhoe75 on 2010-07-22
OK. I repeat what I ve done yesterday and sudo works. I hope bug will never happen when I decide to reconfigure thomething.
But 1 error occures, look:

i1@i1-desktop:~$ gksu nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 255 &#1087;&#1088;&#1080; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1077; 'net usershare': net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
Please ask your system administrator to enable user sharing.


(nautilus:1557): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs

Nautilus-Share-Message: Called "net usershare info" but it failed: &#1054;&#1096;&#1080;&#1073;&#1082;&#1072; 255 &#1087;&#1088;&#1080; &#1079;&#1072;&#1087;&#1091;&#1089;&#1082;&#1077; 'net usershare': net usershare: cannot open usershare directory /var/lib/samba/usershares. Error &#1053;&#1077;&#1090; &#1090;&#1072;&#1082;&#1086;&#1075;&#1086; &#1092;&#1072;&#1081;&#1083;&#1072; &#1080;&#1083;&#1080; &#1082;&#1072;&#1090;&#1072;&#1083;&#1086;&#1075;&#1072;
Please ask your system administrator to enable user sharing.

---

