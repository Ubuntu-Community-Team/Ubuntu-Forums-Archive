---
title: "Tenda W322U V2 &amp; Ubuntu 11.04"
date: 2011-07-20
forum: General Help
---

### Post by cpressland on 2011-07-20
Hi All,

I've just completed a new install of Ubuntu 11.04 on an older machine of mine using a W322U V2 for Wireless.

I've tried downloading the driver from: [http://tendausa.com/Products/WirelessAdapters/USB/W322U/tabid/135/Default.aspx](http://tendausa.com/Products/WirelessAdapters/USB/W322U/tabid/135/Default.aspx)

But get the following errors in the terminal:

```
make -C tools
make[1]: Entering directory `/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools'
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/Makefile
make  -C  /lib/modules/2.6.38-10-generic/build SUBDIRS=/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-10-generic'
  CC [M]  /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.o
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSetEntry’:
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4002:39: warning: operation on ‘Tab->BssOverlapNr’ may be undefined
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c: In function ‘BssTableSortByRssi’:
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/mlme.c:4406:1: warning: the frame size of 1584 bytes is larger than 1024 bytes
  CC [M]  /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/action.o
  CC [M]  /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c: In function ‘RtmpRaDevCtrlInit’:
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3709:2: error: implicit declaration of function ‘init_MUTEX’
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.c:3710:2: warning: passing argument 2 of ‘os_alloc_mem’ from incompatible pointer type
/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/include/rtmp.h:5704:13: note: expected ‘UCHAR **’ but argument is of type ‘UCHAR *’
make[2]: *** [/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/cpressland/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-10-generic'
make: *** [LINUX] Error 2
cpressland@cpressland-PC:~/Desktop/2009_1110_RT3070_Linux_STA_v2.1.2.0$ 

```

I've googled around a lot and a few forums suggest various different Tarballs but they all result in similar errors. Any ideas?

Thanks Guys

Chris

---

### Post by cpressland on 2011-07-20
I also tried this:

[http://ubuntuforums.org/showpost.php?p=10010789&postcount=4](http://ubuntuforums.org/showpost.php?p=10010789&postcount=4)

This compiled and run correctly, but the network manager still shows [firmware missing]

---

### Post by cpressland on 2011-07-20
Nevermind, all I had to do was add the module to /etc/modules and it worked fine.

---

### Post by Paul28799 on 2011-08-07
Hi could you help me here, new to ubuntu but very impressed but having a lot of problems trying to get my Tenda W322U wireless N usb device to work, no led and the built in wireless g on the laptop is the only one working.  As you appear to have got one working could you lead me to getting this working please.  Hope to here from you.  Paul

---

