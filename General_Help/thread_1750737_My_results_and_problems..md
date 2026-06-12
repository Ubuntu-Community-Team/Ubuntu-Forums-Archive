---
title: "My results and problems."
date: 2011-05-05
forum: General Help
---

### Post by mattintc10 on 2011-05-05
I think someone directed me down the wrong path or where to go im not sure but it sure seems to be that way in my Xubuntu 11.04. 

Here is what i got when i had help from my parent in making the binary file or something. 

Heres what it started out as ( system name and user name is matthew confusingly and stupid enough) 

root@matthew:/home/matthew/ndiswrapper-1.8# make
Make -C driver
Make[1]: Entering directory `/home/matthew/ndiswrapper-1.8/driver`
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/home/matthew/ndiswrapper-1. 
8/driver \ 
                                   DRIVER_VERSION=1.8
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
scripts/Makefile.build:49:***CFLAGS was changed in "/home/matthew/ndieswrapper- 
1.8/driver/Makefile". Fix it to use EXTRA_CFLAGS. Stop.
Make[2]: *** [_module_/home/matthew/ndiswrapper-1.8/driver] Error 2
Make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic' 
Make[1]: *** [default] Error 2 
Make[1]: Leaving directory `/home/matthew/ndiswrapper-1.8/driver ' 
Make: *** [all] Error 2

---

### Post by andrewthomas on 2011-05-05
You are definitely going down the wrong path.

You should not be building anything in your home directory as root.

You should be using ndiswrapper-utils-1.9 from the repos.

Follow the squeeze instructions here:

[http://wiki.debian.org/NdisWrapper](http://wiki.debian.org/NdisWrapper)

---

### Post by mattintc10 on 2011-05-05
> **andrewthomas said:**
> You are definitely going down the wrong path.

You should not be building anything in your home directory as root.

You should be using ndiswrapper-utils-1.9 from the repos.

Follow the squeeze instructions here:

[http://wiki.debian.org/NdisWrapper](http://wiki.debian.org/NdisWrapper)

Thank you. You have no idea how nice it is to hear someone agree with me i hope this works il come back and post my results.

---

### Post by Shmantiv_Radio on 2011-05-05
Try this.

```
sudo apt-get update && sudo apt-get -f install ndisgtk && sudo ndisgtk
```

Find the .inf file in your downloaded XP driver and install. Then reboot.

---

