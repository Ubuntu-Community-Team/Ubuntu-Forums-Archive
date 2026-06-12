---
title: "usb wifi install"
date: 2010-11-22
forum: General Help
---

### Post by totallynew on 2010-11-22
i have a usb edimax wifi dongle
following a specific guide for driver install i have stumbled across these errors
the guide says you should not have any errors
but i have and the guide doesn't tell you how to fix them
[http://www.edimax.co.uk/images/Image/FAQ/Wireless/Linux/How%20to%20install%20EW-7711xxx%20_3070_%20on%20Linux%20Ubuntu%2010.4%20platform.pdf]("http://www.edimax.co.uk/images/Image/FAQ/Wireless/Linux/How%20to%20install%20EW-7711xxx%20_3070_%20on%20Linux%20Ubuntu%2010.4%20platform.pdf")
 
i got to here
 
/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function &#8216;usb_buffer_free&#8217;
make[2]: *** [/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/lee/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make: *** [LINUX] Error 2
lee@lee-VirtualBox:~/Desktop/DPO_RT3070_LinuxSTA_V2.3.0.2_20100412$

---

### Post by nothingspecial on 2010-11-23
Do you have build-essential?

---

