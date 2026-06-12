---
title: "apt-get and packages configuration"
date: 2010-07-09
forum: General Help
---

### Post by radu.ro on 2010-07-09
Hi all,

I have managed to write a bunch of BASH scripts which with the proper parameters and setup can build a customized Ubuntu LiveCD. I do have a problem though. As you might have noticed, several packages require that the user perform some configuration operations at the install time which are usually made by inputting data into an ncurses text user interface with some input fields (e.g. mysql-server among others has this kind of install process).

Is there a way to skip this "Package Configuration" part? I am already using ```
apt-get -y install packagename
``` but those ncurses interfaces still pop up. Due to this fact I cannot silently install this kind of packages.

Any ideas?

Thank you!

---

### Post by radu.ro on 2010-07-10
I have solved it using [this]("http://ubuntuforums.org/showpost.php?p=6320719&postcount=3") hint. In my case this variable had to be exported into a chrooted environment, e.g.:

```
chroot *location* su - root -c "export DEBIAN_FRONTEND=noninteractive; apt-get -y -qq install $packages"
```

where $packages holds the list of packages to be installed. Unfortunately the only way that this noninteractive install process works is when apt-get is called by root. sudo didn't help.

---

