---
title: "Running Windows software"
date: 2010-06-05
forum: General Help
---

### Post by melinda on 2010-06-05
I need to run some software that seems to only work with Win2002, XP or greater OS.  

Does Ubuntu have a flawless Windows emulator that is easy to use so I can use the software?

Thanks

---

### Post by radddi on 2010-06-05
The Windows emulator for Linux is Wine. To install it open the terminal (Applications >> Accessories >> Terminal) and type:

```
sudo apt-get install wine
```

It will prompt you for your password and then install. You can find more information in Ubuntu's Community Documentation:

[https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine)

.:CheerS:.

---

### Post by scorp123 on 2010-06-05
You have several options here.

You can try **wine** ... It's sort of an emulator that allows you to run single Windows programs (as opposed to running a complete Windows installation) directly on your Linux desktop. A lot of software and even many games work tip top with it. But not all and not every software. You'd have to try to really find out.

Or if you have a Windows install CD: You could install a complete Windows (the version doesn't really matter; could be XP, Vista, 7, whatever) inside a virtualisation solution such as **virtualbox** ... Virtualbox simulates an entire PC, and Windows would be running alongside your Linux desktop in a single window. You could then install your software inside that virtualbox instance. A lot of software that will not work with "wine" above will  work tip top this way.

You will find both software packages inside your package manager, e.g. ***System > Administration > Synaptic Package Manager***

---

