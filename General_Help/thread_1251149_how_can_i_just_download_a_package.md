---
title: "how can i just download a package"
date: 2009-08-27
forum: General Help
---

### Post by firsttimeuser on 2009-08-27
i am trying to download a package on a network connected box and later copy the downloaded package to another box, what is the command to just download the package using apt-get?

I tried "apt-get -d expect", but it did not work, thanks

---

### Post by coldReactive on 2009-08-27
I suggest downloading manually via the ubuntu package search website:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by ptn107 on 2009-08-27
```
sudo apt-get -d install <package>
```

---

### Post by xebian on 2009-08-27
> **firsttimeuser said:**
> i am trying to download a package on a network connected box and later copy the downloaded package to another box, what is the command to just download the package using apt-get?

I tried "apt-get -d expect", but it did not work, thanks

apt-get -d install expect

It's better to use 

aptitude download pkg-name

---

### Post by fela on 2009-08-27
Is the computer running a GUI? If it is, you can use synaptic aswell.

---

