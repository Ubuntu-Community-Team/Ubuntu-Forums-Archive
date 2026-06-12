---
title: "Diskless ubuntu - testing on VirtualBox"
date: 2010-06-04
forum: General Help
---

### Post by yotamhc on 2010-06-04
Hi,
I am trying to setup a server for diskless ubuntu computer lab. I followed the steps in this manual:
[https://help.ubuntu.com/community/DisklessUbuntuHowto](https://help.ubuntu.com/community/DisklessUbuntuHowto)

As currently I have no other computer to connect to the server and test that it works, I would like to test it by net-booting a virtual machine on it. I am trying to do that with VirtualBox (as I could not get VMWare server to work with my firefox 3.6).

I tried several configurations of the virtual machine's networking but I am probably missing something.

Here are the technical details of my system:
Ubuntu server 10.4 (kernel version 2.6.32-21-server)
DHCP server is set to the subnet 192.168.1.0/24 and range of 192.168.1.2-192.168.1.99 and gateway 192.168.1.1 (which is my router).
My server is connected to the router on a WLAN interface and also has an Ethernet NIC which is not in use.
Currently the router runs a DHCP server (because my family wants internet connection) but I also tried to disable it for a while and rerun the test and it did not work.

The netboot image OS is Ubuntu 10.4 desktop edition.
I am working on getting another physical machine to connect it to the server by Ethernet cable but currently I don't have one available.

Can anyone help me complete the required configuration and get it working?

Thanks,
Yotam

---

### Post by yotamhc on 2010-06-04
OK, I found the (first) problem but don't know how to solve it - I get a "File not found" error from the TFTP server (I booted a livecd in the virtual machine and connected to server with TFTP, then tried to get the pxelinux.0 file (or any other file in /tftpboot) but it always says "File not found".

What else should I do to make the TFTP server work correctly?

Thanks

---

### Post by yotamhc on 2010-06-04
Additional updates:
1. I moved to test it from my Mac laptop using a VMWare fusion virtual machine that boots from network.
2. The VM successfully receives info from DHCP but does nothing afterwards (before, it said "TFTP Transfer timed out")
3. When connecting from another linux VM on that Mac I can successfully connect to the TFTP server and download files from it

I guess it is a simple configuration problem between DHCP and TFTP? I have spent the last hour reading everything I found in google on that issues but could not make it work...

EDITED: Topic moved to servers forum: [http://ubuntuforums.org/showthread.php?t=1501358](http://ubuntuforums.org/showthread.php?t=1501358)

---

