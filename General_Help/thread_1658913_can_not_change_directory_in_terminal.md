---
title: "can not change directory in terminal"
date: 2011-01-03
forum: General Help
---

### Post by dbowlin17 on 2011-01-03
I am using terminal in 10.10. I am trying to install a ps3 eye driver with [http://kaswy.free.fr/?q=en/node/53](http://kaswy.free.fr/?q=en/node/53) when i try to do the cd linux, it says that there is no such file or directory. however, when i type "dir" one of the things that shows up is linux. i am able to get in and out of all the other directories that show up in addition to "linux" but i can't get into "linux"

---

### Post by seawolf167 on 2011-01-03
If this is the part you are having problems with:

```
cd /usr/src
apt-get install linux-source
tar --bzip2 -xvf linux-source-2.6.<your version>.tar.bz2
ln -s linux-2.6.<your version> linux
**cd linux**
```

Try this instead (or hit tab after typing "linux"):

```
cd /usr/src/linux-source-2.6.<your version>
```

ln just makes a link between files, since you have already extracted the files from "linux-source-2.6.<your version>.tar.bz2", the folder will be named "linux-source-2.6.<your version>" because of the -f switch

---

### Post by dbowlin17 on 2011-01-03
thanks. that worked but the rest of the process didn't. oh well, thanks for your help

---

