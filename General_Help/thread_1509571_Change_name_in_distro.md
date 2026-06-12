---
title: "Change name in distro"
date: 2010-06-14
forum: General Help
---

### Post by Stroqq on 2010-06-14
Hello! Sorry of my bad english. Help me, please. We work in school, and create linux distro for her. Manager wanted "Original name for distro", is "Education OS of School Patrik". How change name in distro? "Ubuntu" on "Education OS....". Thanks.

---

### Post by wednesday allfather on 2010-06-14
If you are trying to edit your hostname (e.g. user@hostname as seen in terminal)

edit /etc/hostname

```
sudo nano /etc/hostname
```

and then just rename and reboot

---

### Post by bumanie on 2010-06-14
Follow [this]("http://ubuntumanual.org/posts/143/how-to-change-computer-name-in-ubuntu").

---

### Post by Stroqq on 2010-06-14
This is not it. This "computer name", but we want "distro name". "Ubuntu 10.04" on "Education OS of School Patrik". How "Ubuntu" on "Mint" and etc.

---

### Post by wednesday allfather on 2010-06-14
```
sudo nano /etc/lsb-release
```

here is what is in mine

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04 LTS"

```

I'd take a good backup first.  I'm not sure if this will cause any problems.

---

### Post by Stroqq on 2010-06-14
Thank you. But it is not full decision. We want, absolute change name Ubuntu. in gnome, install livecd, about, etc. It's very stupid. But school's Manager...

---

