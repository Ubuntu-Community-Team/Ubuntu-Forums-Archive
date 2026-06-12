---
title: "mplayer  repo problems with failed dependencies"
date: 2006-05-04
forum: General Help
---

### Post by k420 on 2006-05-04
When i do ```
sudo apt-get install mplayer
```  it wont install mplayer do to failed dependencies my sources.list file look like this```
deb http://download.skype.com/linux/repos/debian/ stable non-free 
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb ftp://ftp.nerim.net/debian-marillat/ sid main 

```

---

### Post by Ramses de Norre on 2006-05-04
I think you need security multiverse packages (which you didn't enable).

---

### Post by k420 on 2006-05-04
any idea what the address for those are

---

### Post by Ramses de Norre on 2006-05-06
The lines with security.ubuntu, add multiverse and universe at the end.

---

