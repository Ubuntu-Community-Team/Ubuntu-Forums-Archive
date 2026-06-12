---
title: "I need a walkthrough on k10 thermal sensors!!!"
date: 2010-02-24
forum: General Help
---

### Post by konspiracy on 2010-02-24
I tried to follow the instructions on some of the sites that I googled but I always run into some error because I don't know how to make it.

[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)

---

### Post by bruno9779 on 2010-02-24
I have compiled those sensors a few months back.

They work fine, not too sensitive but ok, till you get a kernel update and you have to compile them again.

You need to download the componenets and then compile them.

I am going to do all steps in the terminal, including the downloads:

Get ready:

```
mkdir k10temp
cd k10temp
wget http://khali.linux-fr.org/devel/misc/k10temp/Makefile
sudo chmod +x Makefile
wget http://khali.linux-fr.org/devel/misc/k10temp/k10temp.c
```

now make:

```
make
sudo make install
```

all should be fine now.

PS: I had to install linux-image-2.6.31-20-virtual because System.map was missing. Go figure

---

### Post by x33a on 2010-02-24
I heard that the new kernel 2.6.33 has thermal monitoring support for the newer k10 chips.

[http://www.phoronix.com/scan.php?page=news_item&px=ODAxMg](http://www.phoronix.com/scan.php?page=news_item&px=ODAxMg)

---

### Post by bruno9779 on 2010-02-24
> **x33a said:**
> I heard that the new kernel 2.6.33 has thermal monitoring support for the newer k10 chips.

[http://www.phoronix.com/scan.php?page=news_item&px=ODAxMg](http://www.phoronix.com/scan.php?page=news_item&px=ODAxMg)

:popcorn::popcorn::popcorn::popcorn::popcorn::popcorn:

Finally!!!!

Damn, in ubuntu we're still on 2.6.31-20.
I dunno if I a going to put the effort towards recompiling the kernel or towards finally setting up Arch and compile the new kernel then

---

### Post by x33a on 2010-02-25
Arch should be getting the new kernel in a few days. we are on 2.6.32 currently.

---

