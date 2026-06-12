---
title: "Hard drive no longer spins down"
date: 2009-11-04
forum: General Help
---

### Post by Ingenium on 2009-11-04
I upgraded from 9.04 to 9.10, and I had my partitions formatted as ext4 with nodelalloc enabled since I had frequent kernel panics on 9.04 and was experiencing significant data loss. After upgrading, the hard drive would spin down when idle and on battery, just as it did in 9.04. However, after I removed the nodelalloc mount option, it no longer spins down. Shouldn't it be able to spin down more?

---

### Post by khelben1979 on 2009-11-04
Maybe your system lacks [hdparm]("http://en.wikipedia.org/wiki/Hdparm")?

```
sudo apt-get install hdparm
```
to install it and
```
man hdparm
``` for infomration on how to use it.

---

### Post by wojox on 2009-11-04
Could also try:

```
sudo apt-get install ubuntu-laptop-mode
```

> Laptop mode is a Linux kernel feature that allows the system to reduce power
consumption by allowing the hard drive to spin down for longer periods of
time. This package contains a script to control these kernel parameters.

---

### Post by Ingenium on 2009-11-04
hdparm is installed, as is laptop-mode. I have a custom laptop mode setup for a Thinkpad as per here [http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T400)

As I mentioned, it works if nodelalloc is used as a mount option.

---

