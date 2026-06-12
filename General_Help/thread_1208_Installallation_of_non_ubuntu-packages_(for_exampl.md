---
title: "Installallation of non ubuntu-packages (for example mc)"
date: 2004-10-19
forum: General Help
---

### Post by bizzler on 2004-10-19
I like to install mc (midnight commander). Debian has such a packet, ubuntu does not offer this today.

Can I use the debian-package, and what must I do to get this into ubuntu or must I download the sources an compile it from scratch?

Thank you for Help.

---

### Post by Rancoras on 2004-10-19
I think it's in universe.  Look in the FAQ forum for how to enable universe.

---

### Post by normnmiles on 2004-10-19
Rancoras, right.  It's available in universe.

---

### Post by FLeiXiuS on 2004-10-19
Edit your /etc/apt/sources.list with your favorite text editor

sudo vi /etc/apt/sources.list

Add these 2 lines to the list.
```
deb http&#58;//archive.ubuntu.com/ubuntu/ warty main restricted universe 
deb-src http&#58;//archive.ubuntu.com/ubuntu/ warty main restricted universe
```

Afterwards
sudo apt-get update

---

### Post by bizzler on 2004-10-20
Hey, that helps me. Very easy!
Thanks to all, that was it.

Bye,

Bizzler

---

### Post by bandoba on 2007-05-12
I have installed mc on Ubuntu Feisty and it uses proper line drawing characters when I run it inside gnome-terminal. But when I run screen and then run mc, it just never seem to use line drawing characters. I looked at the mc FAQ here ([http://www.ibiblio.org/mc/FAQ](http://www.ibiblio.org/mc/FAQ)) and they have given few reasons why this might be happening. But I don't really think the problem is related to that.

BTW, one strange observation: I have to unset LANG or LANGUAGE variable for mc to show line drawing 
correctly. This is again without screen. But at least it then shows up correctly.

Any ideas?

---

