---
title: "No packages are being installed!"
date: 2006-02-16
forum: General Help
---

### Post by rkakkar on 2006-02-16
$ ls amsn_0.95-3.ubuntu.deb
amsn_0.95-3.ubuntu.deb
$ sudo apt-get install amsn_0.95-3.ubuntu.deb
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package amsn_0.95-3.ubuntu.deb

---

### Post by bluevoodoo1 on 2006-02-16
Try...

```

sudo dpkg -i amsn_0.95-3.ubuntu.deb

```

here's a link with more info... [http://ubuntuforums.org/showthread.php?t=78529&highlight=install+.deb](http://ubuntuforums.org/showthread.php?t=78529&highlight=install+.deb)

---

### Post by rkakkar on 2006-02-16
oh yes of course!! how silly of me!! thanks!

---

