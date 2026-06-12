---
title: "Transferring all downloaded packages to another computer?"
date: 2010-08-20
forum: General Help
---

### Post by ltwinner on 2010-08-20
I am about to go on a last minute trip abroad and I need to bring a laptop with me so Im getting a lend of my mothers one. It has windows 7 and I will be sticking ubuntu on it. The problem is there are alot of programs/packages that I need and I wont have time to download them all. So is it possible to transfer the packages/programs I need from my PC to this laptop?

---

### Post by davrosuk on 2010-08-20
I don't think it is... yet - but apparently Maverick 10.10 will have the ability to do it thru OneConf.

There may be some other "third-party" method that I'm unaware of though.

---

### Post by jfreak_ on 2010-08-20
unless you have cleaned it up, look in /var/apt/cache. All the packages should be there. OIf course, you'll have to install them one by one

---

### Post by ajgreeny on 2010-08-20
Have a look at aptoncd, which may be what you want.  In spite of the name, if one or both of the machines has no CD drive, you can just use the iso file that is made on the donor computer and transfer that to the destination computer and use; it's how I always use the program.

---

