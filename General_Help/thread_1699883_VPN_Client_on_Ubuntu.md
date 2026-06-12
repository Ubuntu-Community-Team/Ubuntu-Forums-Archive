---
title: "VPN Client on Ubuntu"
date: 2011-03-04
forum: General Help
---

### Post by ron177 on 2011-03-04
Dear all,


 I have been having a bit of difficulty installing Cisco VPN Client (IPsec) 4.8 on my Ubuntu 10.10.
 

I have been trying to follow the instructions given here:


 [http://www.shuvoovuhs.com/linux/install-cisco-vpn-client-on-ubuntu-10-10-maverick-meerkat/](http://www.shuvoovuhs.com/linux/install-cisco-vpn-client-on-ubuntu-10-10-maverick-meerkat/)
 

But the problem is that my Cisco VPN Client is called "ciscovpn_x86_64_48000490_k9.tar.gz" and not what is suggested on the above page (vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz).  As a result I have been having difficulties following the instructions  from the first stage where the author says I should put the following  command in the terminal:
 

tar -zxvf vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz
 

Even when I change this command to
 

tar -zxvf ciscovpn_x86_64_48000490_k9.tar.gz
 

I don't get any results. Any thoughts as to how I can go about  downloading this? This is really important to me. I can't get remote  access to my school if I can't install the Cisco VPN software.


 Appreciatively.

---

### Post by seawolf167 on 2011-03-04
*"Assuming you already have the Cisco VPN client (vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz) downloaded."*

So the first step is to download the file. Have you downloaded it?

If you have, where have you saved it? (The default place is ~/Downloads), so lets assume that's where it is.

Open a terminal (Applications -> Accessories -> Terminal)

Change to the Downloads directory (where the file you downloaded is stored)

```
cd ~/Downloads
```Extract the tar.gz file

```
tar -xzf *filenamehere*.tar.gz
```Change to the new directory

```
cd *filenamehere*
```

Continue with his instructions

---

### Post by ron177 on 2011-03-05
> **seawolf167 said:**
> *"Assuming you already have the Cisco VPN client (vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz) downloaded."*

So the first step is to download the file. Have you downloaded it?

If you have, where have you saved it? (The default place is ~/Downloads), so lets assume that's where it is.

Open a terminal (Applications -> Accessories -> Terminal)

Change to the Downloads directory (where the file you downloaded is stored)

```
cd ~/Downloads
```Extract the tar.gz file

```
tar -xzf *filenamehere*.tar.gz
```Change to the new directory

```
cd *filenamehere*
```Continue with his instructions


Hi -- 

Thanks so much for your message. I followed your instructions and then went back to the original instructions given on the above webpage. But at some point I think something has gone wrong. I am pasting the terminal commands for your info if it's at all of some help to figuring out what I have done so far. Please do let me know if there is something I can do to fix the problem as I seem to have installed the software but it's not working still.

ranin@ranin-Satellite-C655:~$ cd -/Downloads
bash: cd: -/: invalid option
cd: usage: cd [-L|-P] [dir]
ranin@ranin-Satellite-C655:~$ cd ~/Downloads
ranin@ranin-Satellite-C655:~/Downloads$ tar -xzf ciscovpn_x86_64_48000490_k9.tar.gz
ranin@ranin-Satellite-C655:~/Downloads$ cd vpnclient
ranin@ranin-Satellite-C655:~/Downloads/vpnclient$ wget [http://files.shuvoovuhs.com/fixes.patch](http://files.shuvoovuhs.com/fixes.patch)
--2011-03-05 05:57:12--  [http://files.shuvoovuhs.com/fixes.patch](http://files.shuvoovuhs.com/fixes.patch)
Resolving files.shuvoovuhs.com... 67.222.5.53
Connecting to files.shuvoovuhs.com|67.222.5.53|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8448 (8.2K) [text/plain]
Saving to: `fixes.patch'

100%[======================================>] 8,448       --.-K/s   in 0.1s    

2011-03-05 05:57:12 (72.5 KB/s) - `fixes.patch' saved [8448/8448]

ranin@ranin-Satellite-C655:~/Downloads/vpnclient$ patch < ./fixes.patch
patching file frag.c
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 22.
2 out of 2 hunks FAILED -- saving rejects to file frag.c.rej
patching file interceptor.c
Hunk #1 FAILED at 9.
Hunk #2 FAILED at 116.
Hunk #3 succeeded at 101 (offset -28 lines).
Hunk #4 succeeded at 219 (offset -28 lines).
Hunk #5 succeeded at 248 (offset -28 lines).
Hunk #6 succeeded at 271 (offset -28 lines).
Hunk #7 FAILED at 659.
Hunk #8 FAILED at 686.
Hunk #9 FAILED at 804.
5 out of 9 hunks FAILED -- saving rejects to file interceptor.c.rej
patching file IPSecDrvOS_linux.c
Hunk #1 FAILED at 12.
1 out of 1 hunk FAILED -- saving rejects to file IPSecDrvOS_linux.c.rej
patching file linuxcniapi.c
Hunk #1 FAILED at 10.
Hunk #2 FAILED at 338.
Hunk #3 FAILED at 478.
Hunk #4 FAILED at 487.
4 out of 4 hunks FAILED -- saving rejects to file linuxcniapi.c.rej
patching file linuxkernelapi.c
patching file Makefile
ranin@ranin-Satellite-C655:~/Downloads/vpnclient$ sudo ./vpn_install
[sudo] password for ranin: 
Cisco Systems VPN Client Version 4.8.00 (0490) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.35-27-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.35-27-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.35-27-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.35-27-generic/build SUBDIRS=/home/ranin/Downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-27-generic'
  CC [M]  /home/ranin/Downloads/vpnclient/linuxcniapi.o
/home/ranin/Downloads/vpnclient/linuxcniapi.c:12: fatal error: linux/config.h: No such file or directory
compilation terminated.
make[2]: *** [/home/ranin/Downloads/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/ranin/Downloads/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-27-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
ranin@ranin-Satellite-C655:~/Downloads/vpnclient$ sudo /etc/init.d/vpnclient_init start
sudo: /etc/init.d/vpnclient_init: command not found
ranin@ranin-Satellite-C655:~/Downloads/vpnclient$ sudo /etc/init.d/vpnclient_init start
sudo: /etc/init.d/vpnclient_init: command not found
ranin@ranin-Satellite-C655:~/Downloads/vpnclient$ vpnclient connect fairfax
vpnclient: command not found
ranin@ranin-Satellite-C655:~/Downloads/vpnclient$

---

### Post by ron177 on 2011-03-05
I think the problem begins when I try to apply the patch I downloaded from the web:
 

ranin@ranin-Satellite-C655:~/Downloads/vpnclient$ patch < ./fixes.patch
patching file frag.c
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 22.
2 out of 2 hunks FAILED -- saving rejects to file frag.c.rej
patching file interceptor.c
Hunk #1 FAILED at 9.
Hunk #2 FAILED at 116.
Hunk #3 succeeded at 101 (offset -28 lines).
Hunk #4 succeeded at 219 (offset -28 lines).
Hunk #5 succeeded at 248 (offset -28 lines).
Hunk #6 succeeded at 271 (offset -28 lines).
Hunk #7 FAILED at 659.
Hunk #8 FAILED at 686.
Hunk #9 FAILED at 804.
5 out of 9 hunks FAILED -- saving rejects to file interceptor.c.rej
patching file IPSecDrvOS_linux.c
Hunk #1 FAILED at 12.
1 out of 1 hunk FAILED -- saving rejects to file IPSecDrvOS_linux.c.rej
patching file linuxcniapi.c
Hunk #1 FAILED at 10.
Hunk #2 FAILED at 338.
Hunk #3 FAILED at 478.
Hunk #4 FAILED at 487.
4 out of 4 hunks FAILED -- saving rejects to file linuxcniapi.c.rej
patching file linuxkernelapi.c
patching file Makefile

---

### Post by seawolf167 on 2011-03-05
> **ron177 said:**
> But the problem is that my Cisco VPN Client is called  "ciscovpn_x86_64_48000490_k9.tar.gz" and not what is suggested on the  above page (vpnclient-linux-x86_64-4.8.02.0030-k9.tar.gz)

> **ron177 said:**
> I think the problem begins when I try to apply the patch I downloaded from the web:

The patch is probably not designed for the version or source that you are working with, which is why you are getting the errors. Patches are very picky, even slightly different versions of a program will give you errors.

---

