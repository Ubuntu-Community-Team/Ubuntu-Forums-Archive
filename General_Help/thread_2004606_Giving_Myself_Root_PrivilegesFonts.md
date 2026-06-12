---
title: "Giving Myself Root Privileges/Fonts"
date: 2012-06-16
forum: General Help
---

### Post by SerFaren on 2012-06-16
I am the only login user on my computer, and yet, I still have no root privileges. I am trying to install a font, but it continuously tells me I cannot gain access to /usr/share/fonts/truetype

Any help is appreciated! Thanks!

---

### Post by 3rdalbum on 2012-06-16
> **SerFaren said:**
> I am the only login user on my computer, and yet, I still have no root privileges. I am trying to install a font, but it continuously tells me I cannot gain access to /usr/share/fonts/truetype

Any help is appreciated! Thanks!

That's correct, there's no "root" user on Ubuntu. However, your first login account has the ability to use 'sudo' to gain root privileges on a program-by-program basis.

To run a command as root, simply put the word "sudo" and a space before the command you want to run, for instance:

```
sudo apt-get update
```

For a graphical program, you use "gksudo":

```
gksudo nautilus
```

The above command runs the file browser "nautilus" as root. Since the file browser is running as root, you can use it to modify system files, and put fonts into "/usr/share/fonts/truetype". Of course, anything done outside that particular window will still be done as an ordinary user, and anything done in the window will be done as root. BE CAREFUL. Open a root file browser ONLY for privileged operations, and close it straight afterward. Don't use it for ordinary things or you will mess up the permissions in your home directory.

---

### Post by Erik1984 on 2012-06-16
You need sudo to obtain temporary root privileges.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/RootSudo#Usage](https://help.ubuntu.com/community/RootSudo#Usage)

---

