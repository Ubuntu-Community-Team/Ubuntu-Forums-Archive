---
title: "VMware 2.0 server ubuntu"
date: 2011-03-31
forum: General Help
---

### Post by timothyinthehouse on 2011-03-31
Hello!

I keep getting this error when it asks me for the c header files:

what is the location of the directory of c header files that match your running kernel? [/usr/src/linux/include]

I've tried to install things like sudo apt-get install build-essential, but it seems that everything is updated?...

Now I am stuck, if I do things like: /usr/src/linux-2.6.35-28-generic/include

or remove -generic and add -server .

I get another error:

The directory of kernel headers (version 2.6.35-28-generic) does not match your running kernel (version 2.6.35-28-server). Even if the module were to compile successfully, it would not load intro the running kernel.

So what do I have to do?

~ Timothy

---

### Post by davidmohammed on 2011-03-31
have a look here for a step by step [guide]("http://www.howtoforge.com/how-to-install-vmware-server-2-on-ubuntu-10.10-kernel-2.6.35") - you'll notice that you'll need to install the correct headers for the kernel.

---

