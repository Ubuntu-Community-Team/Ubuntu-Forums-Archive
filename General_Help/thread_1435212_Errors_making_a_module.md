---
title: "Errors making a module"
date: 2010-03-21
forum: General Help
---

### Post by desmogod on 2010-03-21
I can hook my way around linux pretty well but sometimes something just stumps me.
Like this, I'm sure it's a very easy fix or I'm overlooking something.
Trying to install [this]("http://http://rc.zexos.org"), and have followed the instructions, but this happens....

```
jim@Ubuntu-9:~/Desktop/txppm/module$ sudo make 
make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
jim@Ubuntu-9:~/Desktop/txppm/module$ sudo make install
make -C /lib/modules/`uname -r`/build M=`pwd` modules_install
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-20-generic'
  INSTALL /home/jim/Desktop/txppm/module/tx.ko
  DEPMOD  2.6.31-20-generic
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
jim@Ubuntu-9:~/Desktop/txppm/module$ modprobe tx
FATAL: Module tx not found.

```

Any help greatly appreciated, I'm tearing my hair out.

---

### Post by rnerwein on 2010-03-21
hi
why should modprobe search for that module "tx" in ~/Desktop/txppm/module ?
 modprobe  looks  in  the  module  directory  /lib/modules /`uname  -r`  for  all  the modules and other files, except for the optional  /etc/modprobe.conf  configuration  file  and  /etc/modprobe.d
ciao

---

### Post by JorgeB500 on 2010-05-05
Did you ever solve this, I am having the same problem and do not know how to create /dev/tx with mknod
The readme says to check dmesg but im not sure what to look for.

---

### Post by robertspil on 2010-05-11
I am trying to use txppm.
I compile the module with the steps (as root terminal)
make
make install
insmode tx.ko (  not  modprobe )
then dmesg gives the needed information:
input: PPM Transmitter as /devices/virtual/input/input9
Use: 'mknod /dev/tx c 250 0'.
mknod /dev/tx c 250 0
then
chmod +w /dev/tx
create a directory for the tx.ko (/lib/modules/2.6.32-22-generic/kernel/drivers/tx )
copy the module, but this is not enough : after a reboot the module is not loaded !
a depmode -a solves this question. Now the module is loaded after a reboot
Robert

---

### Post by JorgeB500 on 2010-05-11
That worked for me, module now loads no problem. Thanks for the detailed install instructions.

---

