---
title: "libgtk-1.2.so.0: cannot open shared object file: No such file or directory"
date: 2010-09-06
forum: General Help
---

### Post by OpressedCalamity on 2010-09-06
Hello - 
Whenever I try to install a game thats in a .run file format, I get the following error.
libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I am trying to install Unreal Tournament.
What can I do to resolve this issue?
Thanks.

---

### Post by psavva on 2010-09-06
> **OpressedCalamity said:**
> Hello - 
Whenever I try to install a game thats in a .run file format, I get the following error.
libgtk-1.2.so.0: cannot open shared object file: No such file or directory

I am trying to install Unreal Tournament.
What can I do to resolve this issue?
Thanks.


Install libgtk-1.2

```

sudo apt-get update
sudo apt-get install libgtk-1.2

```

---

### Post by BbUiDgZ on 2010-09-06
> **psavva said:**
> Install libgtk-1.2

```

sudo apt-get update
sudo apt-get install libgtk-1.2

```
see [here](http://ubuntuforums.org/showthread.php?t=474790)

i know with enemy-territory i had to make a sybolic link for some of my libs because of the file name the game was looking for, for example
```
ln -s /usr/lib/name_of_real_lib /usr/lib/name_the_game_wants
```
the above is not the exact command as i have no idea what the actual lib is called and if your on a x64 build or not

---

### Post by OpressedCalamity on 2010-09-06
I can't install libgtk, I get the following error.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libgtk-1.2
soledad@Vredesbyrd-Perverse:~$

---

### Post by Soulcage on 2010-09-20
There's no package for karmic or lucid you have to download the files from jaunty [http://packages.ubuntu.com/jaunty/libgtk1.2]("http://packages.ubuntu.com/jaunty/libgtk1.2")
libgtk1.2 libglib1.2ldbl libgtk1.2-common you need atleast those 3 and there's no telling if it will work with this particular package. I know libstdc++5 does work. (ut2004)

---

