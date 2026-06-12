---
title: "ndiswrapper build problem"
date: 2006-02-15
forum: General Help
---

### Post by Bakerconspiracy on 2006-02-15
This is what happens after i run the make install command. It will not install correctly and i have no idea what to do about this error.

root@homeNet:/home/andrew/ndiswrapper-1.10# make install
make -C driver install
make[1]: Entering directory `/home/andrew/ndiswrapper-1.10/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/andrew/ndiswrapper-1.10/driver'
make: *** [install] Error 2
root@homeNet:/home/andrew/ndiswrapper-1.10#

I can never seem to get this program to work the right way....

---

### Post by nanotube on 2006-02-15
i think ndiswrapper is by default available in ubuntu, without need for install...

---

### Post by Bakerconspiracy on 2006-02-15
root@homeNet:/home/andrew/ndiswrapper-1.10# ndiswrapper -i
bash: ndiswrapper: command not found

Nope. Thanks though.

---

### Post by nanotube on 2006-02-16
```
$ modprobe -n -v ndiswrapper
insmod /lib/modules/2.6.12-10-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko

```
so yes, the kernel module IS there by default.

what is not there by default is the userspace tools (such as the running of ndiswrapper from your commandline). to install that, just install the package "ndiswrapper-utils", which is available from synaptic.

so try that, i think it will solve your problems.

---

### Post by kaamos on 2006-02-16
You will need the headers to build
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by gremlin hunter on 2006-02-16
You just need to install ndiswrapper-utils from the CD.

---

