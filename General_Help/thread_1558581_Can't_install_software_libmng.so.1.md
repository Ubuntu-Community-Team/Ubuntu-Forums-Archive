---
title: "Can't install software: libmng.so.1"
date: 2010-08-22
forum: General Help
---

### Post by brian515 on 2010-08-22
Hi all,

I'm new to Linux, and am trying to virtualize a guest install of Ubuntu in Virtualbox on top of OS X. The install proceeded fine, and I installed the guest additions. However, when I go to install software via an autopackage, it fails libmng.so.1 so the software won't install. 

I don't know what to do because I'm a linux newbie. I'd greatly appreciate any help in advance.

Thanks a ton!

---

### Post by dougalkerr on 2010-08-22
If you can open a Terminal in your Ubuntu guest system then type 

'sudo apt-get install libmng.so.1' without the little single quotes.

In a normal system sudo will give you root (admin) privileges allowing installation of software and packages. This may be all you need. Others may give you a better answer.
It won't do any harm to try...

---

### Post by brian515 on 2010-08-22
Thanks for the reply, but that didn't work. Here's what I got.


Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package libmng.so.1

---

### Post by stoneage on 2010-08-22
That's not surprising.

libmng.so.1 is a file provided by the package libmng1

Check to see if it is installed.

---

### Post by dougalkerr on 2010-08-22
Since you are a newbee to Linux just substitute the filename from the previous reply in the 'sudo apt-get instal...' line that I gave you and if all goes well, everything should install.

---

### Post by brian515 on 2010-08-22
Great, thanks guys. That worked!

---

### Post by dougalkerr on 2010-08-22
Glad to be of help...

---

