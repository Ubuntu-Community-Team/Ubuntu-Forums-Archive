---
title: "Problem installing NoMachine's NX server"
date: 2010-03-15
forum: General Help
---

### Post by MacGoose on 2010-03-15
Hi!

I'm having problems installing NoMachine's NX server.  I had one install of this package that went very wrong so I kinda have it semi installed already causing more problems.

Anyway, have installed the client and the node.  So trying to install the server I just get an error saying the NX user already exist - please uninstall.  So I try to uninstall.  Getting an error saying that it's not installed and I have to install it first.

Talk about being stuck in a loop.  So I try to remove the NX user manually and see if that will fix it.  Problem here is that I can't find any NX user to remove.  What do I do...?  Where is that NX user hiding...?

Man I wish that developers would just supply some sort of installer packages.  Installing and configuring LAMP was very easy compared to some of the programs you get for Linux - and I would say LAMP is one of the more advanced packages around...

, MacGoose

---

### Post by prodigy_ on 2010-03-15
Try:
```
sudo rm /etc/init.d/nxserver
```
```
sudo rm /var/lib/dpkg/info/nxserver.*
```

---

### Post by 2hot6ft2 on 2010-03-15
Once you have the messed up install removed you should be using this guide for installing the FreeNX server.
Installing FreeNX
[http://help.ubuntu.com/community/FreeNX](http://help.ubuntu.com/community/FreeNX)

---

### Post by MacGoose on 2010-03-15
Thanx!

Though none of the above worked.  Removing the files did not help.  And trying to install FreeNX generated some errors and what looked like a crash report.

I'll do this at a later time when I'm gonna do a fresh upgrade of 9.10.  It seems that this install has been corrupted and wont go either way to let me install or uninstall...

, MacGoose

---

### Post by pricetech on 2010-03-15
I ran into that a few months ago, but don't remember the solution.  Check the documentation from No Machine and I'll look to see if I can find some notes.

---

### Post by prodigy_ on 2010-03-15
Hmm. I'm not very familiar with how dpkg operates. Perhaps it stops when it encounters non-empty directories? A more thorough cleanup might be needed then. Something like ```
sudo find / -name nx*
``` may help.

Or you can try to install .tar.gz version. Maybe it's less picky.

---

