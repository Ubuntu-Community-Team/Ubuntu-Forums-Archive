---
title: "How do you get and install SuperTuxKart?"
date: 2010-05-04
forum: General Help
---

### Post by 2048Megabytes on 2010-05-04
How do you get and install SuperTuxKart for Ubuntu 9.04?

---

### Post by moviemaniac on 2010-05-04
It should be available in Synaptic from the universe repo: [http://packages.ubuntu.com/search?keywords=supertuxkart&searchon=names&suite=jaunty&section=all](http://packages.ubuntu.com/search?keywords=supertuxkart&searchon=names&suite=jaunty&section=all)

---

### Post by bigsmitty64 on 2010-05-04
Its in the software center too, I just checked :)

---

### Post by darolu on 2010-05-04
And finally you can also install via command line with:
```
$ sudo apt-get install supertuxkart
```

---

### Post by cuberts on 2010-05-04
**Linux**

For GNU/Linux you can see if an up-to-date package is  available for your distro - depending on distro try: 

[LIST]
[*] apt-get install supertuxkart
[*] aptitude install supertuxkart
[*] or for Fedora:  yum install supertuxkart
[*] or for Gentoo  emerge supertuxkart
[*] or for [UHU]("http://distrowatch.com/table.php?distribution=uhu") get it at [http://uhu.linux.hu/](http://uhu.linux.hu/)
[*] For SuSE Linux / openSUSE, you can add the games:/action  repository and then install supertuxkart using your favourite tool  (YaST, rug, zen-installer, zypper, smart). SuperTuxKart is built for  SuSE i586 and x86_64. There are 2 known repositories:
[LIST]
[*][http://ftp-1.gwdg.de/pub/opensuse/repositories/games:/action/](http://ftp-1.gwdg.de/pub/opensuse/repositories/games:/action/)  then browse to your Linux Version.
[*][http://download.opensuse.org/repositories/games:/arcade/](http://download.opensuse.org/repositories/games:/arcade/).
[/LIST]
 
[/LIST]
Alternatively, download the binary tarball from the [STK Download area]("http://sourceforge.net/project/showfiles.php?group_id=202302")


```

tar -xjvf supertuxkart_bin_x86_linux.tar.bz2
cd supertuxkart-0.6

```
also do this to run stk

```

run_game.sh

```

---

### Post by 2048Megabytes on 2010-05-05
I figured it out.  Just go to the below website and click on the link it installs itself and works:

[https://help.ubuntu.com/community/Games](https://help.ubuntu.com/community/Games)

---

