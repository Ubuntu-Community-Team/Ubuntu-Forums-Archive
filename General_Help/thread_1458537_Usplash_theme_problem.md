---
title: "Usplash theme problem"
date: 2010-04-20
forum: General Help
---

### Post by i.arnav on 2010-04-20
I installed the mac theme in ubuntu 9.04 bt step bt step method given on this site:
[http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08]("http://maketecheasier.com/turn-your-ubuntu-intrepid-into-mac-osx-leopard/2009/01/08")

But i am facing problem in running the osx-splash theme.

_Following below mentioned code gives error that **sudo: splashy_config: command not found**_

```
sudo splashy_config –i ~/osx-splash.tar.gz
sudo mv /etc/splashy/config.xml /etc/splashy/config.xml.old
sudo cp /etc/splashy/themes/osx-splash/config.xml /etc/splashy/config.xml
```

how do solve this problem and run the code smoothly.

---

### Post by _0R10N on 2010-04-20
Well, it seems like you haven't installed the splashy_config command, that's probably because you haven't installed the splashy package either. You should install it first, as I posted in a thread you opened along with this one.

Kind regards!!

_0R10N >>

---

### Post by mcduck on 2010-04-20
Your problem is that Usplash and Splashy are two completely different applications... ;)

---

### Post by i.arnav on 2010-04-20
thnx for replying sir, but whenever i try installing splashy package it shows following error:
[I]
E: /var/cache/apt/archives/splashy_0.3.13-3ubuntu1_i386.deb: trying to overwrite `/etc/lsb-base-logging.sh', which is also in package lsb-base[/I]

---

