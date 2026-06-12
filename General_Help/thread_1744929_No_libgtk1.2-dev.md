---
title: "No libgtk1.2-dev"
date: 2011-04-30
forum: General Help
---

### Post by augustuen on 2011-04-30
I just downloaded the Putty source code to compile the latest version, only to get an error saying I didn't have GTK1.2-dev installed. "Simple enough," I thought, "I'll just install it with apt-get!". Only to find out that libgtk1.2-dev is no longer in the repository. 

**How can I install libgtk1.2-dev??**

---

### Post by mc4man on 2011-04-30
Start here, also work back on the listed deps you can't satisy, stick them all in a folder, cd to the folder and
```
sudo dpkg -i *.deb

```

You need 5 in all - Ex. for 32 bit
> libglib1.2-dev_1.2.10-19build1_i386.deb  
libglib1.2ldbl_1.2.10-19build1_i386.deb  
libgtk1.2-dev_1.2.10-18.1build2_i386.deb
libgtk1.2_1.2.10-18.1build2_i386.deb
libgtk1.2-common_1.2.10-18.1build2_all.deb

[http://packages.ubuntu.com/hardy/libgtk1.2-dev](http://packages.ubuntu.com/hardy/libgtk1.2-dev)

---

