---
title: "Problem with /etc/hosts"
date: 2006-06-17
forum: General Help
---

### Post by Zikes on 2006-06-17
In trying to set up an LTS server following the directions [here]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") I made some changes to my hosts file.  Unfortunately I made an error and now seem to have lost administrative privileges and can't change it back.  I backed up the hosts file, but without root access I can't fix anything.

```
zikes@zikes-desktop:~$ sudo cp /etc/hosts_backup /etc/hosts
sudo: unable to lookup zikes-desktop via gethostbyname()
```

As far as I know I'm not able to log in as root in Ubuntu, is there any other way  to fix it?

---

### Post by aysiu on 2006-06-17
You can definitely log in as root. Just reboot into recovery mode, and you'll be root.

---

### Post by Zikes on 2006-06-17
aha!  Thank you kindly :D

---

### Post by viniosity on 2006-06-22
I'm having the same issue but I don't have physical access to the box.. only ssh.  I can't even reboot because everytime I run a command with su I get that unable to lookup via gethostbyname() error.

Am I stuck?

---

### Post by mlind on 2006-06-22
[QUOTE=viniosity]I'm having the same issue but I don't have physical access to the box.. only ssh.  I can't even reboot because everytime I run a command with su I get that unable to lookup via gethostbyname() error.

Am I stuck?[/QUOTE]

try recovery option on grub boot menu. You should somehow get to runlevel 1,
where you will automatically be logged as root.

---

### Post by scxtt on 2006-06-22
[QUOTE=mlind]try recovery option on grub boot menu. You should somehow get to runlevel 1,
where you will automatically be logged as root.[/QUOTE]he most likely won't be able to edit menu.lst to even do that, and even if he could - i really doubt recovery mode starts the sshd ...

---

### Post by mlind on 2006-06-22
[QUOTE=scxtt]he most likely won't be able to edit menu.lst to even do that, and even if he could - i really doubt recovery mode starts the sshd ...[/QUOTE]

ah, forgot the ssh only.. I don't see any other chance than booting that machine
and getting to runlevel 1 if init/telinit are restricted from normal users
and root account is "disabled"

---

