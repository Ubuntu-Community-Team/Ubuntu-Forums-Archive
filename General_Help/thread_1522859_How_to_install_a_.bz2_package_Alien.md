---
title: "How to install a .bz2 package? Alien?"
date: 2010-07-02
forum: General Help
---

### Post by bliffle on 2010-07-02
Can't find my notes or .sh for installing a .bz2 file. As I recall I used 'alien', before. The actual file is latest 'vuze' if that makes a difference.

How do I install that .bz2 file?

---

### Post by Vaphell on 2010-07-02
it's an archive, unpack it and there are some shell scripts inside.
also you can look for a premade .deb file, like this
[http://www.getdeb.net/software/Azureus](http://www.getdeb.net/software/Azureus)

azureus is vuze, right?

---

### Post by bliffle on 2010-07-05
I unpacked it and ran the "vuze.sh" and it seems to have installed, with a few messages. Actually, quite a few messages, which I have captured.

---

### Post by Crazedpsyc on 2010-07-05
Umm, just wondering: what is Alien? I hope it's not important bcuz I am planning to use that name lol!

---

### Post by WorMzy on 2010-07-05
[http://en.wikipedia.org/wiki/Alien_%28software%29](http://en.wikipedia.org/wiki/Alien_%28software%29)

---

### Post by bodhi.zazen on 2010-07-05
Alien is a method of converting rpm or other packages to .deb

In general you will want to use alien as a last resort, use the Ubuntu repositories first, then source code.

[http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/)

You do not "install" a .bz2 , just as you do not install a zip file . A bz2 is an archive, like a zip.

You go to the home page of the package you wish to install and read the README.

Some archives contain source code which is then compiled, others contain install scripts, others contain the binaries.

[http://wiki.vuze.com/w/Initial_Setup_Guide](http://wiki.vuze.com/w/Initial_Setup_Guide)

---

### Post by Crazedpsyc on 2010-07-05
Oh, package conversion. thanks! mine is going to be a gtk theme

---

