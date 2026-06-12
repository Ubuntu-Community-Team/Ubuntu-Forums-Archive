---
title: "ram upgrade"
date: 2010-04-12
forum: General Help
---

### Post by wcutrombonekid on 2010-04-12
so i upgraded my ram a while back.  I went from 1 GB to 4GBs.  sooo much nicer when i'm forced to use windows, it also makes ubuntu speedier than it already was.

My issue is this, since i upgraded, my windows partition remarkably recognizes all 4 gigs, I expected it would max out at like 3.5 since its 32 bit and all.  anyway, my ubuntu partition only recognizes 2.7.  Is there anyway to increase what it sees without upgrading to 64 bit?

---

### Post by jedlacks on 2010-04-12
I believe the short answer is no.  A smarter person will give a longer answer and maybe another will give you a work around if any.

---

### Post by elliotn on 2010-04-12
a u sure ur mobo takes up to 4gig coz some mobo have limit.

---

### Post by darolu on 2010-04-12
After you check what ellioth said; you can try installing the server kernel with:
```
$ sudo apt-get install linux-server
```
You *may* need to edit the configuration file of your kernel:
```
$ gksu gedit /boot/config-2.6...
```
Search for the lines with: HIGHMEM

Learn more: [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by techstop on 2010-04-12
> **wcutrombonekid said:**
> ...my windows partition remarkably recognizes all 4 gigs, I expected it would max out at like 3.5 since its 32 bit and all.  anyway, my ubuntu partition only recognizes 2.7.  Is there anyway to increase what it sees without upgrading to 64 bit?

Windows may "recognize" 4GB of RAM on a 32-bit system, but I guarantee you it's not using it all. From Vista SP2, they changed the way the System Properties displayed so that users with 32-bit systems and 4GB of RAM could see that 4GB is installed. If you open the Task Manager, you will see that somewhat less than 4GB is actually available for use.

---

### Post by 3rdalbum on 2010-04-12
> **techstop said:**
> Windows may "recognize" 4GB of RAM on a 32-bit system, but I guarantee you it's not using it all. From Vista SP2, they changed the way the System Properties displayed so that users with 32-bit systems and 4GB of RAM could see that 4GB is installed. If you open the Task Manager, you will see that somewhat less than 4GB is actually available for use.

+1. Microsoft kept getting complaints that "Windows isn't recognising all my RAM", so they changed it in Vista SP1 to report the total installed RAM, even if some of it is inaccessible.

You can install the Linux Server kernel which uses PAE to get "36-bit addressing", but from what I hear it doesn't work with ATI's graphics drivers.

You'll probably never fill your 2.7 gigabytes of addressable memory on Ubuntu anyway; but the next time you do a fresh install of Ubuntu you should just use the 64-bit edition.

---

### Post by wcutrombonekid on 2010-04-15
> **3rdalbum said:**
> +1. Microsoft kept getting complaints that "Windows isn't recognising all my RAM", so they changed it in Vista SP1 to report the total installed RAM, even if some of it is inaccessible.

You can install the Linux Server kernel which uses PAE to get "36-bit addressing", but from what I hear it doesn't work with ATI's graphics drivers.

You'll probably never fill your 2.7 gigabytes of addressable memory on Ubuntu anyway; but the next time you do a fresh install of Ubuntu you should just use the 64-bit edition.

when i upgrade to 10/04, can i upgrade to 64 bit, or do i need to do a fresh install?

---

