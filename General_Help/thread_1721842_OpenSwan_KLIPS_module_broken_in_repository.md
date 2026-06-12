---
title: "OpenSwan KLIPS module broken in repository"
date: 2011-04-05
forum: General Help
---

### Post by andygauvin.ee on 2011-04-05
Looks like I'm attempting to revive more than a few dead threads with this one...

I'm attempting to install KLIPS support for my OpenSwan installation.

```
# apt-get install openswan-modules-dkms

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  openswan-modules-dkms
0 upgraded, 1 newly installed, 0 to remove and 58 not upgraded.
Need to get 0B/565kB of archives.
After this operation, 3,138kB of additional disk space will be used.
Selecting previously deselected package openswan-modules-dkms.
(Reading database ... 273707 files and directories currently installed.)
Unpacking openswan-modules-dkms (from .../openswan-modules-dkms_1%3a2.6.26+dfsg-1_all.deb) ...
Setting up openswan-modules-dkms (1:2.6.26+dfsg-1) ...
Loading new openswan-2.6.26+dfsg DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-27-generic-pae
Building for architecture i686
Building initial module for 2.6.35-27-generic-pae

Error! Bad return status for module build on kernel: 2.6.35-27-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/openswan/2.6.26+dfsg/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/openswan-modules-dkms.0.crash'
dpkg: error processing openswan-modules-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 openswan-modules-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


Please advise?

---

### Post by andygauvin.ee on 2011-04-05
More relevant info:
```
# uname -a
Linux amaya 2.6.35-27-generic-pae #48-Ubuntu SMP Tue Feb 22 21:46:58 UTC 2011 i686 GNU/Linux
```
```

# cat /var/lib/dkms/openswan/2.6.26+dfsg/build/make.log 
DKMS make.log for openswan-2.6.26+dfsg for kernel 2.6.35-27-generic-pae (i686)
Tue Apr  5 03:05:26 EDT 2011
make: Entering directory `/var/lib/dkms/openswan/2.6.26+dfsg/build'
make[1]: Entering directory `/var/lib/dkms/openswan/2.6.26+dfsg/build'
mkdir -p /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26
echo ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/des/*.S /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/des/dx86unix.S /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26
(rm -f /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/des; mkdir -p /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/des && cd /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/des && ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/des/* . && ln -s -f Makefile.fs2_6 Makefile)
(rm -f /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/aes; mkdir -p /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/aes && cd /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/aes && ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/aes/* . && ln -s -f Makefile.fs2_6 Makefile)
mkdir -p /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/aes
cp /var/lib/dkms/openswan/2.6.26+dfsg/build/packaging/makefiles/module26.make /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/Makefile
echo "# "                        >> /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/Makefile
echo "# Local Variables: "       >> /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/Makefile
echo "# compile-command: \"make -C /var/lib/dkms/openswan/2.6.26+dfsg/build ARCH=i386 KERNELSRC=/lib/modules/2.6.35-27-generic-pae/build MOD26BUILDDIR=/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26 module26\""         >> /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/Makefile
echo "# End: "       >> /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/Makefile
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/match*.S /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26
make[1]: Leaving directory `/var/lib/dkms/openswan/2.6.26+dfsg/build'
make -C /lib/modules/2.6.35-27-generic-pae/build  BUILDDIR=/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26 SUBDIRS=/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26 MODULE_DEF_INCLUDE=/var/lib/dkms/openswan/2.6.26+dfsg/build/packaging/linus/config-all.h MODULE_DEFCONFIG=/var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/defconfig  MODULE_EXTRA_INCLUDE= ARCH=i386 V= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-27-generic-pae'
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_init.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_init.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_init.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_sa.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_sa.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_sa.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_radij.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_radij.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_radij.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/radij.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/radij.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/radij.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_life.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_life.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_life.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_proc.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_proc.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_proc.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_tunnel.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_tunnel.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_tunnel.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_xmit.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_xmit.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_xmit.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_rcv.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_rcv.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_rcv.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_ipip.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_ipip.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_ipip.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_snprintf.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_snprintf.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_snprintf.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/ipsec_mast.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_mast.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/ipsec_mast.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/sysctl_net_ipsec.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/sysctl_net_ipsec.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/sysctl_net_ipsec.o
ln -s -f /var/lib/dkms/openswan/2.6.26+dfsg/build/linux/net/ipsec/pfkey_v2.c /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.c
  CC [M]  /var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.o
/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.c:135: warning: initialization from incompatible pointer type
/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.c: In function ‘pfkey_create’:
/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.c:723: error: ‘struct socket’ has no member named ‘fasync_list’
/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.c:723: error: ‘struct sock’ has no member named ‘sk_sleep’
/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.c: In function ‘pfkey_get_info’:
/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.c:1160: error: ‘struct sock’ has no member named ‘sk_sleep’
make[2]: *** [/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26/pfkey_v2.o] Error 1
make[1]: *** [_module_/var/lib/dkms/openswan/2.6.26+dfsg/build/modobj26] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-27-generic-pae'
make: *** [module26] Error 2
make: Leaving directory `/var/lib/dkms/openswan/2.6.26+dfsg/build'


```

---

### Post by andygauvin.ee on 2011-04-05
My gift to the world! I hope this helps out all those unsolved, deceased threads I've come across...

Uninstall all current ubuntu-repo attemps at openswan:

```
sudo apt-get remove openswan* openswan-modules*
```

Download the official Xelerance version packaged for Ubuntu:
(I only had reliable luck with version 2.6.32-1xelerance1)

i386:
```
wget ftp://ftp.openswan.org/openswan/binaries/ubuntu/openswan-modules-dkms_2.6.32-1xelerance1_i386.deb ftp://ftp.openswan.org/openswan/binaries/ubuntu/openswan-doc_2.6.32-1xelerance1_all.deb ftp://ftp.openswan.org/openswan/binaries/ubuntu/openswan_2.6.32-1xelerance1_i386.deb
sudo dpkg -i ./openswan-doc_2.6.32-1xelerance1_all.deb ./openswan_2.6.32-1xelerance1_i386.deb
sudo dpkg -i ./openswan-modules-dkms_2.6.32-1xelerance1_i386.deb

```

amd64:
```
wget ftp://ftp.openswan.org/openswan/binaries/ubuntu/openswan-modules-dkms_2.6.32+1-1xelerance1_amd64.deb ftp://ftp.openswan.org/openswan/binaries/ubuntu/openswan_2.6.32+1-1xelerance1_amd64.deb ftp://ftp.openswan.org/openswan/binaries/ubuntu/openswan-doc_2.6.32-1xelerance1_all.deb
sudo dpkg -i ./openswan_2.6.32+1-1xelerance1_amd64.deb ./openswan-doc_2.6.32-1xelerance1_all.deb
sudo dpkg -i ./openswan-modules-dkms_2.6.32+1-1xelerance1_amd64.deb

```

Restart openswan to enable the newly patched-in KLIPS DKMS kernel module:
```
sudo /etc/init.d/ipsec restart
```

... and if all goes will you'll see:

```
ipsec_setup: Stopping Openswan IPsec...
ipsec_setup: Starting Openswan IPsec 2.6.32...
ipsec_setup: ipsec0 -> NULL mtu=0(0) -> 0
```

for every kernel automagically thereafter!


PLEASE google, pick this one up and spread it to the masses.

---

