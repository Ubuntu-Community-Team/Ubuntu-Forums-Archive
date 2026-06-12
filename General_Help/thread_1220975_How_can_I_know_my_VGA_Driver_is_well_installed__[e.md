---
title: "How can I know my VGA Driver is well installed ? [effects doesn't work]"
date: 2009-07-23
forum: General Help
---

### Post by drdigital on 2009-07-23
HI All, 
I'm still new :d to ubuntu. I wanted to do 2 things, the first is to run compiz effects and the second is to run avant window navigator.The two trials failed and I think I have a problem in my VGA Driver.so:

how can I make sure my driver is working well ?
how can I install it in case it has a problem ?

My VGA is built-in M.B: GigaByte945

---

### Post by wojox on 2009-07-23
What does System > Administration > Hardware Drivers say?

---

### Post by drdigital on 2009-07-23
NO thing !
No Proprietary drivers are in use on this system
Empty boxes

---

### Post by 3rdalbum on 2009-07-23
"Gigabyte945" - does that mean you are using Intel graphics?

There's been a bit of a situation with the Intel graphics drivers that are installed by default in Ubuntu 9.04. Intel is in the process of rewriting the driver, and the performance and stability of the driver is currently not as good as it used to be. This will change in future, and in fact some Intel graphics cards have improved since the release of Ubuntu 9.04.

If so, run all system updates first, and reboot. If your card is one that has been improved since April, then you may regain use of Compiz.

Otherwise, try the suggestions given on this page: [http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html]("http://webupd8.blogspot.com/2009/04/ubuntu-jaunty-904-intel-graphic-drivers.html"). I can't guarantee anything from this HOWTO; I've never tried it, I just found it by looking for "compiz intel ubuntu 9.04" on Google.

---

