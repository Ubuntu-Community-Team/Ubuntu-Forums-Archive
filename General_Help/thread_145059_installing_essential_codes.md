---
title: "installing essential codes"
date: 2006-03-15
forum: General Help
---

### Post by styven on 2006-03-15
Hi all,

I am trying to install the the essential codec pack and am getting the following result.....

styven@edubuntu:~$ cd /usr/lib
styven@edubuntu:/usr/lib$ sudo tar xfvj/desktop/essential-20050412.tar.bz
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
styven@edubuntu:/usr/lib$ sudo tar xfvj/desktop/essential-20050412.tar.bz2
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
styven@edubuntu:/usr/lib$

I am following instruction from the magazine personal computer world so would expect this to work, am i missing a trick here?

Steve.

---

### Post by Xian on 2006-03-15
Try this:
$ sudo tar -xvpjf name_of_archive.tar.bz2

I'm not quite certain of your paths, but that's another story.

---

### Post by kronepils on 2006-03-15
The 'f' option has to be the last before the filename, e.g. tar jxvf sdf.tar.bz2 should do the trick...

---

### Post by Sutekh on 2006-03-15
[QUOTE=styven]
styven@edubuntu:/usr/lib$ sudo tar xfvj/desktop/essential-20050412.tar.bz

am i missing a trick here?
[/QUOTE]
Yep a space.

Try
```
sudo tar xvjf /desktop/essential-20050412.tar.bz
```

---

