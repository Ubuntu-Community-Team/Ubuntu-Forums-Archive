---
title: "root error"
date: 2010-01-03
forum: General Help
---

### Post by senorsalsa99 on 2010-01-03
So i have just  switched to ubuntu!!
anyways my problem is i installed ubuntu set up a password etc etc,
i installed some software but everytime i run it it says i need to be root
so i open up comand prompt i type in su, it asks for the password i type in my password and i get an authentication error.

---

### Post by SuperSonic4 on 2010-01-03
Ubuntu does not enable the root account by default, instead it is suggested you preface any command you need to be root for with *sudo*. For example

```
sudo apt-get install
```

To repeat the last command issued as root: ```
sudo !!
```

You *can* enable the root but telling you is against forum policy - [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---------------------------------------

It is possible to edit sudo related things in /etc/sudoers if you need to grant another user access by name. I edited mine to let me use make install without a password for example because I compile from SVN a lot

---

