---
title: "I need Linux kernel 3"
date: 2011-09-15
forum: General Help
---

### Post by elliotn on 2011-09-15
I need the repository of kernel 3, I mean way to install it and later get its updates if available, I just need it for curiosity reasons, my machine works good.

---

### Post by chukchuck on 2011-09-15
Here you are:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

Enjoy :)

---

### Post by elliotn on 2011-09-15
thanks bro alot

---

### Post by elliotn on 2011-09-15
uhmmmmm how do I add that to the repos coz repos were suppose to start with deb HTTP:// blah blah .....

---

### Post by sanderd17 on 2011-09-15
just put 'deb' before it I guess.

---

### Post by sanderd17 on 2011-09-15
Damn, double post

---

### Post by elliotn on 2011-09-16
I did add deb but upon reloading the repos the was a error, something like unsigned ppa or something like key.

---

### Post by garvinrick4 on 2011-09-16
You want to install a kernel? 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Choose which one you want from list of kernels (click on it)
and you will get 5 choices:
all.deb
32 bit headers
64 bit headers
32 bit image
64 bit image

Take the all.deb
your choice of 32 or 64 bit headers and image

Download those 3 and click on:
all.deb
headers
image
in that order and will install thru software center they are all in .deb already.
If any problems installing can do from command line.
Drop the 3 .deb packages on Desktop
cd Desktop
ls
sudo dpkg -i (copy and paste all.deb
sudo dpkg -i (copy and paste headers)
sudo dpkg -i (copy and paste image)
You now have new kernel to boot from.

---

### Post by realzippy on 2011-09-16
Last time I tried kernel ppa was down,means,it did not work for some reason.
Maybe due to the hack?
Installing kernel manually works...

---

### Post by garvinrick4 on 2011-09-16
Works right now, just downloaded one to see.
[http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.4-oneiric/](http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.4-oneiric/)

---

### Post by elliotn on 2011-09-16
> **garvinrick4 said:**
> You want to install a kernel? 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
Choose which one you want from list of kernels (click on it)
and you will get 5 choices:
all.deb
32 bit headers
64 bit headers
32 bit image
64 bit image

Take the all.deb
your choice of 32 or 64 bit headers and image

Download those 3 and click on:
all.deb
headers
image
in that order and will install thru software center they are all in .deb already.
If any problems installing can do from command line.
Drop the 3 .deb packages on Desktop
cd Desktop
ls
sudo dpkg -i (copy and paste all.deb
sudo dpkg -i (copy and paste headers)
sudo dpkg -i (copy and paste image)
You now have new kernel to boot from.

the this is with that method I may not get updates. I need to get the kernel updates as soon as they are available

---

