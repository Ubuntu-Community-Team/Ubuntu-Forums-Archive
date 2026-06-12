---
title: "How to make a debian package?"
date: 2012-02-08
forum: General Help
---

### Post by MrBandicootKid on 2012-02-08
I want to know how to do it but I have no clue where to start. Can someone explain like step by step how to do it? and what to type in terminal or script?

---

### Post by Rafterman414 on 2012-02-08
After you extract the source files for the package you want to make go to the folder that they are in and type

```
./configure
``````
make
``````
checkinstall
```Checkinstall is what will make the debian package for you. Make sure you have the following packages installed on your system, gcc, build-essentials, checkinstall and probably a few others, I'm sure other people can shed some light on this as well since I just started doing this recently. Also if apt stops working for you check in your software sources for 
file:/var/cache/apt-build/repository
I had that in mine after making some packages and I think it was caused by making the .deb's it broke apt:
You can check my thread at [http://ubuntuforums.org/showthread.php?t=1922461](http://ubuntuforums.org/showthread.php?t=1922461) to see about the issue I had.

Here is a good how-to on the matter: [Building .deb packages]("http://chris.olstrom.com/howto/build-deb-packages-from-source/")
Another how-to: [How to create a .deb package from source]("http://community.linuxmint.com/tutorial/view/162")

---

### Post by Cheesemill on 2012-02-09
Check out the links on this page:

[http://developer.ubuntu.com/packaging/html/](http://developer.ubuntu.com/packaging/html/)

---

### Post by Habitual on 2012-02-09
[http://www.debian-administration.org/articles/336](http://www.debian-administration.org/articles/336)
[http://www.debian-administration.org/articles/337](http://www.debian-administration.org/articles/337)

---

