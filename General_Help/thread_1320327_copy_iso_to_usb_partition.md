---
title: "copy iso to usb partition"
date: 2009-11-09
forum: General Help
---

### Post by n00ne on 2009-11-09
I'm trying to create multiple live-cd boot usb
following this guide -
[http://psychoticspoon.blogspot.com/2009/01/booting-multiple-livecds-from-single.html](http://psychoticspoon.blogspot.com/2009/01/booting-multiple-livecds-from-single.html)

but when I try to copy the iso the drive I get permission error -
sudo cat nameOfImage1.iso > /dev/sdb5

bash: /dev/sdb5: Permission denied

I'm using ubuntu 9.10 if it matters.

10x

---

### Post by coffeecat on 2009-11-09
> **n00ne said:**
> but when I try to copy the iso the drive I get permission error -
sudo cat nameOfImage1.iso > /dev/sdb5

bash: /dev/sdb5: Permission denied

You get a permission denied message if you use 'sudo cat....', but if you use a root terminal without sudo you'll be OK.

Try:

```
sudo -i
```... to get a root terminal, and then..

```
cat nameofimage.iso > /dev/sdb5
```By the way, if you use 'sudo -i' you'll be in root's home, and you'll either have to cd or put in the full path to the ISO. If you want to remain in your home, get a root terminal with:

```
sudo su
```

---

### Post by scragar on 2009-11-09
I always thought dd was the prefered method to pipe data around to raw devices.

---

### Post by n00ne on 2009-11-09
10x
it's warking now.

isn't dd and cat the same ?

---

### Post by scragar on 2009-11-09
> **n00ne said:**
> 10x
it's warking now.

isn't dd and cat the same ?

Cat is just used for reading files, dd is used for reading and writing directly to block devices, like say a pen drive.

---

