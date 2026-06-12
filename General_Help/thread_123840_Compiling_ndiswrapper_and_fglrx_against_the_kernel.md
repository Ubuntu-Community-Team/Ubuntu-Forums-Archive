---
title: "Compiling ndiswrapper and fglrx against the kernel"
date: 2006-01-31
forum: General Help
---

### Post by nelposto on 2006-01-31
Hii,

I'm having problems compiling ndiswrapper for my new kernel .. (with suspend2 hibernate support) 

I'm trying to compile ndiswrapper1.8 for my 2.6.12 based vanilla kernel, with no luck.
> 
ryan@ryan:/usr/src/ndiswrapper-1.8$ sudo make
make -C driver
make[1]: Entering directory `/usr/src/ndiswrapper-1.8/driver'
make -C /lib/modules/2.6.12-hibernate.framebufferniegro/build SUBDIRS=/usr/src/ndiswrapper-1.8/driver \
        DRIVER_VERSION=1.8
make[2]: Entering directory `/usr/src/linux-source-2.6.12'
  LD      /usr/src/ndiswrapper-1.8/driver/built-in.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/hal.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/iw_ndis.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/loader.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/misc_funcs.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/ndis.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/ntoskernel.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/ntoskernel_io.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/pe_linker.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/pnp.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/proc.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/wrapndis.o
  CC [M]  /usr/src/ndiswrapper-1.8/driver/wrapper.o
/usr/src/ndiswrapper-1.8/driver/wrapper.c:151:57: macro "create_singlethread_workqueue" requires 2 arguments, but only 1 given
/usr/src/ndiswrapper-1.8/driver/wrapper.c: In function `wrapper_init':
/usr/src/ndiswrapper-1.8/driver/wrapper.c:151: error: `create_singlethread_workqueue' undeclared (first use in this function)
/usr/src/ndiswrapper-1.8/driver/wrapper.c:151: error: (Each undeclared identifier is reported only once
/usr/src/ndiswrapper-1.8/driver/wrapper.c:151: error: for each function it appears in.)
make[3]: *** [/usr/src/ndiswrapper-1.8/driver/wrapper.o] Error 1
make[2]: *** [_module_/usr/src/ndiswrapper-1.8/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.12'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/usr/src/ndiswrapper-1.8/driver'
make: *** [all] Error 2

I also have troubles compiling what looks to be my actuall wireless driver, into the kernel .. giving these errors:

> drivers/built-in.o: In function `alloc_ieee80211':
: undefined reference to `ieee80211_crypt_deinit_handler'
drivers/built-in.o: In function `free_ieee80211':
: undefined reference to `ieee80211_crypt_quiescing'
drivers/built-in.o: In function `free_ieee80211':
: undefined reference to `ieee80211_crypt_deinit_entries'
drivers/built-in.o: In function `ieee80211_wx_set_encode':
: undefined reference to `ieee80211_crypt_delayed_deinit'
drivers/built-in.o: In function `ieee80211_wx_set_encode':
: undefined reference to `ieee80211_crypt_delayed_deinit'
drivers/built-in.o: In function `ieee80211_wx_set_encode':
: undefined reference to `ieee80211_get_crypto_ops'
drivers/built-in.o: In function `ieee80211_wx_set_encode':
: undefined reference to `ieee80211_get_crypto_ops'
drivers/built-in.o: In function `ieee80211_wx_set_encode':
: undefined reference to `ieee80211_crypt_delayed_deinit'
make: *** [.tmp_vmlinux1] Error 1


Incredibly frustrating after having go suspend2 to work fairly happilly, I'm now unable to use wireless with it :( 

Any hints would be much appreciated.

(2.6.12 kernel, Pentium M 2.01, Ubuntu 5.10 Gnome .. )


.. Oops, included fglrx in the title .. Hopefully I can work that out myself though.

---

