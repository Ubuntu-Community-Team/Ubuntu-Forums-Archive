---
title: "Problem with Wireless USB Adapter"
date: 2006-03-03
forum: General Help
---

### Post by victorcete on 2006-03-03
Hi! i'm spanish and my english is very bad xD

I have a Wireless USB Adapter, the model is: SMC2862W-G
this is the web: [http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_GBR&pid=1345](http://www.smc.com/index.cfm?event=viewProduct&localeCode=EN_GBR&pid=1345)

with this manual: [http://www.ubuntu-es.org/node/2895](http://www.ubuntu-es.org/node/2895) , i've install ndiswrapper, the drivers from windowsxp,...


$tar xzf ndiswrapper-1.1.tar.gz
$cd ndiswrapper-1.1
$./configure
$make
[INDENT]~/Desktop/ndiswrapper-1.11rc1$ make
make -C driver
make[1]: Entering directory `/home/atrus/Desktop/ndiswrapper-1.11rc1/driver'
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/atrus/Desktop/ndiswrapper-1.11rc1/driver \
        DRIVER_VERSION=1.11rc1
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make[1]: Leaving directory `/home/atrus/Desktop/ndiswrapper-1.11rc1/driver'
make -C utils
make[1]: Entering directory `/home/atrus/Desktop/ndiswrapper-1.11rc1/utils'
make[1]: No se hace nada para `all'.
make[1]: Leaving directory `/home/atrus/Desktop/ndiswrapper-1.11rc1/utils'[/INDENT]
$sudo make install
[INDENT]
~/Desktop/ndiswrapper-1.11rc1$ sudo make install
make -C driver install
make[1]: Entering directory `/home/atrus/Desktop/ndiswrapper-1.11rc1/driver'
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/atrus/Desktop/ndiswrapper-1.11rc1/driver \
        DRIVER_VERSION=1.11rc1
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  Building modules, stage 2.
  MODPOST
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
mkdir -p /lib/modules/2.6.12-10-386/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.12-10-386/misc
/sbin/depmod -a 2.6.12-10-386
make[1]: Leaving directory `/home/atrus/Desktop/ndiswrapper-1.11rc1/driver'
make -C utils install
make[1]: Entering directory `/home/atrus/Desktop/ndiswrapper-1.11rc1/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/atrus/Desktop/ndiswrapper-1.11rc1/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
[/INDENT]
$ndiswrapper -i /usr/local/drivers/SMC2862W.inf
[INDENT]
~/Desktop/ndiswrapper-1.11rc1$ sudo ndiswrapper -i /usr/local/drivers/SMC2862W.inf
Installing smc2862w
[/INDENT]
$ndiswrapper -l

[INDENT]$ ndiswrapper -l
Installed drivers:
smc2862w                driver installed, hardware present
[/INDENT]
$modprobe ndiswrapper
[INDENT]modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
[/INDENT]
how root:
$modprobe ndiswrapper
[INDENT]sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted
[/INDENT]

someone knows de error?!

thanks!

---

### Post by HumBug on 2006-03-03
It's not very clear at the end. Did you enter :

_sudo_ modprobe ndiswrapper ?

and i think it's better if you install the inf driver also as root as well. So first delete it and reinstall it:

sudo ndiswrapper -i /usr/local/drivers/SMC2862W.inf

---

