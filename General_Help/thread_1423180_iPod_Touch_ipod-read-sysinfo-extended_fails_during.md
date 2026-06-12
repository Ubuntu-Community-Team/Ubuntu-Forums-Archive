---
title: "iPod Touch: ipod-read-sysinfo-extended fails during setup"
date: 2010-03-06
forum: General Help
---

### Post by digitalhead on 2010-03-06
I am trying to setup an iPod Touch 3G with firmware 3.1.3 and following instructions from [here](http://www.taranfx.com/sync-iphone-linux) with the exception of installing libimobiledevice0 and libimobiledevice-dev instead of the libiphone-utils, libiphone0, python-iphone. (libimobiledevice replaced libiphone)

On step 6, where it says to run "ipod-read-sysinfo-extended" I do that and it comes up with this... 
```
$ ipod-read-sysinfo-extended 33545feca44e0e9589bc6d070327bc19e1b7cda9 /mnt/ipod

** (process:4734): WARNING **: Compiled without libimobiledevice support, can't read SysInfoExtended from an iPhone UUID
Couldn't read xml sysinfo from 33545feca44e0e9589bc6d070327bc19e1b7cda9
```

Any suggestions on resolving this? I've been trying for 2 weeks to be able to add music to my iPod from my computer with no luck at all. It gets rather annoying having to transfer my music to a flash drive in order to add music from a Windows computer.

---

