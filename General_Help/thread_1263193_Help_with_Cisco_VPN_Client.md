---
title: "Help with Cisco VPN Client"
date: 2009-09-10
forum: General Help
---

### Post by BURMAT on 2009-09-10
New here.. Just wanted to say this forum has provided me with so much help dealing with my problems. I just registered here because this is one problem I have not been able to solve by searching.

Before I am allowed to connect to my wireless here on campus, I have to download Cisco VPN client v4.6.00.045. The linux version of this is unsupported here though. I am running Ubuntu 9.04, GNOME 2.26.1, and Kernel 2.6.28-15-generic. I understand that there is a patch for Kernels 2.6+ but nothing seems to be working for me. I will post again the errors and everything I get from the failed install without the patch. Any help is greatly appreciated in advance.

-Nathan

---

### Post by BURMAT on 2009-09-10
USER@ubuntu:~$ cd Desktop/vpnclient 
 USER@ubuntu:~/Desktop/vpnclient$ sudo ./vpn_install 
 [sudo] password for USER:  
 Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer 
 Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved. 

 By installing this product you agree that you have read the 

 license.txt file (The VPN Client license) and will comply with 
 its terms. 
  
 Directory where binaries will be installed [/usr/local/bin] 
  
 Automatically start the VPN service at boot time [yes] 
  
 In order to build the VPN kernel module, you must have the 
 kernel headers for the version of the kernel you are running. 
  
 Directory containing linux kernel source code [/lib/modules/2.6.28-15-generic/build] 
  
 * Binaries will be installed in "/usr/local/bin". 
 * Modules will be installed in "/lib/modules/2.6.28-15-generic/CiscoVPN". 
 * The VPN service will be started AUTOMATICALLY at boot time. 
 * Kernel source from "/lib/modules/2.6.28-15-generic/build" will be used to build the module.
  
 Is the above correct [y] 

 Making module 
 make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/USER/Desktop/vpnclient modules 
 make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic' 
   CC [M]  /home/USER/Desktop/vpnclient/linuxcniapi.o 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:12:26: error: linux/config.h: No such file or directory 
 In file included from /home/USER/Desktop/vpnclient/Cniapi.h:15, 
                  from /home/USER/Desktop/vpnclient/linuxcniapi.c:34: 
 /home/USER/Desktop/vpnclient/GenDefs.h:114: error: conflicting types for ‘uintptr_t’ 
 include/linux/types.h:40: error: previous declaration of ‘uintptr_t’ was here 
 /home/USER/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’: 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:315: error: ‘struct sk_buff’ has no member named ‘stamp’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:347: error: ‘struct sk_buff’ has no member named ‘nh’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:348: error: ‘struct sk_buff’ has no member named ‘mac’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’: 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:456: error: ‘struct sk_buff’ has no member named ‘mac’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:457: error: ‘struct sk_buff’ has no member named ‘nh’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘h’ 
 /home/USER/Desktop/vpnclient/linuxcniapi.c:460: error: ‘struct sk_buff’ has no member named ‘nh’ 
 make[2]: *** [/home/USER/Desktop/vpnclient/linuxcniapi.o] Error 1 
 make[1]: *** [_module_/home/USER/Desktop/vpnclient] Error 2 
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic' 
 make: *** [default] Error 2 
 Failed to make module "cisco_ipsec.ko". 
 USER@ubuntu:~/Desktop/vpnclient$ [http://ubuntuforums.org/showthread.php?t=1052065](http://ubuntuforums.org/showthread.php?t=1052065)

---

### Post by Whiffle on 2009-09-10
Have you tried vpnc and network-manager-vpnc in the repository?  I use network-manager-vpnc to connect to the office and it works reasonably well.  

Oh and for some reason, after you add the vpn to network-manager, you have to restart network manager with
sudo /etc/init.d/NetworkManager restart

---

### Post by BURMAT on 2009-09-10
I just don't think any other kind of network manager will work on campus.. I will give a couple more things a try though I guess..

Thanks for your input

-Nathan

---

### Post by Whiffle on 2009-09-10
Well, vpnc is made for cisco vpn's, which is what you need.  Network-Manager-vpnc is just a plugin for the Network-Manager on Linux, to make it easy.  

Here's some more info:

[http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html](http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html)

---

### Post by Chronon on 2009-09-11
> **Whiffle said:**
> Well, vpnc is made for cisco vpn's, which is what you need.  Network-Manager-vpnc is just a plugin for the Network-Manager on Linux, to make it easy.  

Here's some more info:

[http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html](http://www.ubuntugeek.com/how-to-setup-cisco-vpn-using-vpnc-ubuntu-jaunty-9-04.html)

The computing center at my campus encourages us to use Cisco vpnclient too but I use vpnc to log in without any trouble.

---

### Post by dcstar on 2009-09-11
> **Chronon said:**
> The computing center at my campus encourages us to use Cisco vpnclient too but I use vpnc to log in without any trouble.

I use Kvpnc to get around various restrictions the Cisco client has - it works fine.

---

### Post by BURMAT on 2009-09-11
Alright thanks guys! I'll give it a try today and see what happens

-Nathan

---

### Post by bluelamp999 on 2009-09-11
I have this working on 8.10.

It needs to be patched, these are the instructions I followed...

[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/)

I know it's for an ancient release but the concept worked fine on Intrepid.

---

### Post by shylent on 2009-09-11
Well, as I can see, when cisco vpn client tries to compile, it is unable to find a file. Can you verify, that the file it refers to (linux/config.h under you kernel source directory), is indeed there?

Either way, vpnc (and, consequently, kvpnc, the gui) is terrible, compared to the native Cisco VPN client. It doesn't even support ipsec over tcp and I've found it to be extremely unstable (compared to the native client that is). I'd say, for the sake of your own sanity, you try and stick to the native client, you are one step from making it work anyway :)

---

