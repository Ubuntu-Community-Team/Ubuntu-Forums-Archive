---
title: "Install usb wireless adapter billion 3011N"
date: 2010-07-18
forum: General Help
---

### Post by knowlittle on 2010-07-18
Hi, 
I recently install and use ubuntu 10.04 for the first time and having lots of challenges! :mad:
I hope someone can help me out. 
I read up a little and found a makefile in the download that Billion provided. In Terminal, this how far I proceed: 

ty@ty-laptop:~/Downloads$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-23-generic'
  CC [M]  /home/ty/Downloads/HAL/rtl8192u/r8192U_core.o
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c: In function &#8216;rtl8192_usb_probe&#8217;:
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c:12317: error: &#8216;struct net_device&#8217; has no member named &#8216;open&#8217;
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c:12318: error: &#8216;struct net_device&#8217; has no member named &#8216;stop&#8217;
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c:12319: error: &#8216;struct net_device&#8217; has no member named &#8216;tx_timeout&#8217;
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c:12320: error: &#8216;struct net_device&#8217; has no member named &#8216;do_ioctl&#8217;
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c:12321: error: &#8216;struct net_device&#8217; has no member named &#8216;set_multicast_list&#8217;
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c:12322: error: &#8216;struct net_device&#8217; has no member named &#8216;set_mac_address&#8217;
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c:12323: error: &#8216;struct net_device&#8217; has no member named &#8216;get_stats&#8217;
/home/ty/Downloads/HAL/rtl8192u/r8192U_core.c:12324: error: &#8216;struct net_device&#8217; has no member named &#8216;hard_start_xmit&#8217;
make[2]: *** [/home/ty/Downloads/HAL/rtl8192u/r8192U_core.o] Error 1
make[1]: *** [_module_/home/ty/Downloads/HAL/rtl8192u] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-23-generic'
make: *** [all] Error 2

Could someone please tell me what are wrong and how to fix them? 

Thank you in advance.

Well, since I am a n00b I have tried and used Ndiswrapper. It works. Still, I like to know how to make it work in natively Ubuntu.

---

