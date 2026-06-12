---
title: "dpkg: what cause the warning message?"
date: 2010-03-24
forum: General Help
---

### Post by luofeiyu on 2010-03-24
everytime  i use the command

sudo apt-get install
there is the output:

(Reading database ...
dpkg: warning: files list file for package `ruby1.9.1-full' missing, assuming package has no files currently installed.
(Reading database ... 5%
dpkg: warning: files list file for package `libruby' missing, assuming package has no files currently installed.
(Reading database ... 15%
dpkg: warning: files list file for package `ruby-dev' missing, assuming package has no files currently installed.
(Reading database ... 30%
dpkg: warning: files list file for package `libopenssl-ruby1.9.1' missing, assuming package has no files currently installed.
(Reading database ... 45%
dpkg: warning: files list file for package `ruby1.9.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libruby1.8' missing, assuming package has no files currently installed.
(Reading database ... 50%
dpkg: warning: files list file for package `ruby1.8' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libgdbm-ruby1.9.1' missing, assuming package has no files currently installed.
(Reading database ... 55%
dpkg: warning: files list file for package `ruby1.9.1-examples' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libzlib-ruby' missing, assuming package has no files currently installed.
(Reading database ... 60%
dpkg: warning: files list file for package `libyaml-ruby' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libdbm-ruby1.9.1' missing, assuming package has no files currently installed.
(Reading database ... 65%
dpkg: warning: files list file for package `libruby1.9.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libruby1.9.1-dbg' missing, assuming package has no files currently installed.
(Reading database ... 70%
dpkg: warning: files list file for package `libtcltk-ruby1.9.1' missing, assuming package has no files currently installed.
(Reading database ... 75%
dpkg: warning: files list file for package `ruby1.9.1-dev' missing, assuming package has no files currently installed.
(Reading database ... 95%
dpkg: warning: files list file for package `libreadline-ruby1.9.1' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `ruby1.8-dev' missing, assuming package has no files currently installed.
i want to know what cause the warning message?what can i do?

---

### Post by plucky on 2010-03-24
From a terminal **Applications > Accessories > Terminal**
```
sudo dpkg --configure -a
``` and see what that produces.

Good Luck

---

### Post by zvacet on 2010-03-24
```
sudo apt-get -f install
```

or

```
sudo apt-get --fix-missing
```

---

