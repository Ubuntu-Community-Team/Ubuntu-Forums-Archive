---
title: "anyone please"
date: 2010-12-19
forum: General Help
---

### Post by freefixkorma on 2010-12-19
hi guys is there i way how to install google earth i try everything and nothing i am running a acer aspire5742 laptop 64bit on ubuntu 10.10 dktop edition i will appreciate any help

freefix

---

### Post by Frogs Hair on 2010-12-19
This may be some help.[http://ubuntuforums.org/showthread.php?t=1633653&highlight=install+google+earth](http://ubuntuforums.org/showthread.php?t=1633653&highlight=install+google+earth)

---

### Post by kgarbutt on 2010-12-19
Hi, from the terminal type:

sudo apt-get install googleearthsudo lsb-core

and Google Earth will get installed. It is in the Ubuntu Repositories.

---

### Post by oldos2er on 2010-12-19
[http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed](http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed)

---

### Post by karthick87 on 2010-12-19
Add the following to the software sources.
  > deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free  After adding,type the following in terminal
```
sudo apt-get update
```
```
sudo apt-get install googleearth
```

---

### Post by I'mGeorge on 2010-12-19
If you wanna install the bin file from googleearth's official site this it's the way

```

sudo apt-get install ia32-libs ia32-libs-dev ia32-libs-gtk

```

after this download and install the googleearth.bin as a normal user and not as root

```

chmod a+x googleearth.bin
./googlearth.bin

```

This it's an alternative if you've didn't managed to install the package provided from your repos.

---

### Post by freefixkorma on 2010-12-20
thanks for all the help i finally got it right i follow this guide and bang is working like charm thanks again

```
[HTML]http://www.liberiangeek.net/2010/09/install-google-earth-ubuntu-10-10-maverick-meerkat/[/HTML]
```

---

