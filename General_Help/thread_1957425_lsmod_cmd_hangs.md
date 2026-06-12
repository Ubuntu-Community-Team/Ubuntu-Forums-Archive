---
title: "lsmod cmd hangs"
date: 2012-04-12
forum: General Help
---

### Post by smee204 on 2012-04-12
I compiled and installed a kernel dvb module but the hardware was faulty so I removed it. Now the pc does not work correctly. Lots of services seem to not start at boot. Also if I type lsmod in the terminal the terminal just hangs and Ctrl + C will not kill it. 

My syslog contains the following quite a lot:
SERVER udevd[604]: timeout: killing '/sbin/modprobe -bv pci:v00008086d00001C20sv00001043sd0000841Bbc04sc03i00' [610]

My dmesg contains the following a lot:

 83.061411] composite sync not supported
[   83.061416] composite sync not supported
[   83.061418] stereo mode not supported

Any ideas what is going wrong or how to fix it?
My full dmesg is at [http://pastebin.com/sgPhTEdM](http://pastebin.com/sgPhTEdM)

Thanks

---

