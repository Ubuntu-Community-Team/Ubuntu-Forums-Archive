---
title: "Avoid typing a password on every admin action?"
date: 2010-07-15
forum: General Help
---

### Post by mgp2010 on 2010-07-15
How can I avoid typing a password on every admin action? example when i install a program.

---

### Post by 3Miro on 2010-07-15
You might be able to set up an empty password or editing some files, but honestly the password is there for a reason. Enter a very simple password that is easy to type and remember, but keep a password. Otherwise it is like running windows without an AV program.

---

### Post by WorMzy on 2010-07-15
What you're asking is to strip away a layer of security that Linux OS' provide, and this is inadvisable.

Still, if you understand the risks and want to proceed anyway, open up a terminal and run
```
sudo EDITOR=nano visudo
```

Scroll down to the line which says something like
```
<YOURNAME> ALL=(ALL) ALL
```
and change it to
```
<YOURNAME> ALL=(ALL) NOPASSWD:ALL
```

Press Ctrl+X to exit, and say "Y" to the question about saving. If you made a mistake in the file, it'll tell you so, and you'll need to fix it before it'll allow you to save.

---

### Post by 98cwitr on 2010-07-15
what you're asking is not a good idea to do.

---

### Post by nothingspecial on 2010-07-15
> **WorMzy said:**
> What you're asking is to strip away a layer of security that Linux OS' provide, and this is inadvisable.

Still, if you understand the risks and want to proceed anyway, open up a terminal and run
```
sudo EDITOR=nano visudo
```Scroll down to the line which says something like
```
<YOURNAME> ALL=(ALL) ALL
```and change it to
```
<YOURNAME> ALL=(ALL) NOPASSWD:ALL
```Press Ctrl+X to exit, and say "Y" to the question about saving. If you made a mistake in the file, it'll tell you so, and you'll need to fix it before it'll allow you to save.


Rather than do that you can add specific commands that you use alot, that can`t do much damage using visudo.

Read [this]("https://help.ubuntu.com/community/Sudoers")

A better idea than no password ever, for anything.

---

### Post by sisco311 on 2010-07-15
> **mgp2010 said:**
> How can I avoid typing a password on every admin action? example when i install a program.

Create a new config file:
```
gksu gedit /var/lib/polkit-1/localauthority/50-local.d/software-center.pkla
```
with the following content:
```

[Installing software]
Identity=unix-group:admin
Action=org.debian.apt.install-packages;org.debian.apt.update-cache
ResultActive=yes

```

Save the file and exit. This will allow anyy user from the admin group to install software via Software Center without a password.

Removing software and adding repositories will still require password authentication.

Be careful when installing software from third-party repositories. It may not have been tested with Ubuntu and could cause your system to break.

If you want to disable the password for apt-get, check out [thread=1132821]HowTO: Sudoers Configuration[/thread]

---

### Post by oldos2er on 2010-07-15
Use ```
sudo -i
```
Type **exit** when done.

---

### Post by lisati on 2010-07-15
Some have already expressed the opinion that it's not a good idea, with which I concur.

Suggested reading: 
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

