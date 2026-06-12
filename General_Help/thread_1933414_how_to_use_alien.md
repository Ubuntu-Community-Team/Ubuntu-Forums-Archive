---
title: "how to use alien"
date: 2012-02-29
forum: General Help
---

### Post by sinaphysics on 2012-02-29
I want to use alien command to make a deb file from Kile's source code ( latex software and the file is in tar.gz form ).
I was successful in generating it and then I install it. But now I don't know how to operate the installed program. when I type he "kile" name in unity It hasn't any result.
what do u suggest for me?

---

### Post by Gremlinzzz on 2012-02-29
Alien doesn't use tar.gz

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

---

### Post by Gremlinzzz on 2012-02-29
you will need  sudo apt-get install build-essential

better site:popcorn:
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)

checkout 
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
explains the different install methods

use psychocats site others after reading are old

---

### Post by haqking on 2012-02-29
> **Gremlinzzz said:**
> Alien doesn't use tar.gz

[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

yes it can.

alien is not great but can convert .deb to .rpm and vice versa and tar.gz to .deb and .rpm etc.

```
sudo alien -d nameoftarball.tar.gz
```

see ```
man rpm
```

or see here [http://www.newlinuxuser.net/convert-tgz-to-deb-using-alien.html](http://www.newlinuxuser.net/convert-tgz-to-deb-using-alien.html)

however there is also checkinstall.

but if you are just wanting to install the program then far better to install from source or find a .deb or from software centre

---

### Post by Gremlinzzz on 2012-02-29
> **haqking said:**
> yes it can.

alien is not great but can convert .deb to .rpm and vice versa and tar.gz to .deb and .rpm etc.

```
sudo alien -d nameoftarball.tar.gz
```

or see here [http://www.newlinuxuser.net/convert-tgz-to-deb-using-alien.html](http://www.newlinuxuser.net/convert-tgz-to-deb-using-alien.html)

however there is also checkinstall.

but if you are just wanting to install the program then far better to install from source or find a .deb or from software centre

good to know never used alien thought it was for rpm only:popcorn:

---

### Post by haqking on 2012-02-29
> **Gremlinzzz said:**
> good to know never used alien thought it was for rpm only:popcorn:

it does rpm to deb to tgz to slp or back the other way

peace

---

### Post by sinaphysics on 2012-02-29
sorry it was tar.bz2

---

### Post by haqking on 2012-02-29
> **sinaphysics said:**
> sorry it was tar.bz2

tar is a packagin/archiving tool/format the bit on the end either gz or .bz2 means that tarball is compressed thats all.

If you decompress it you will have the tarball/contents

[https://help.ubuntu.com/community/CompilingEasyHowTo#Step_2:_Getting_the_software_you_want](https://help.ubuntu.com/community/CompilingEasyHowTo#Step_2:_Getting_the_software_you_want)

read the rest of the document about compiling from source though

and see here for latex [https://help.ubuntu.com/community/LaTeX](https://help.ubuntu.com/community/LaTeX)

---

