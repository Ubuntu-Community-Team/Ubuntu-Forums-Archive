---
title: "LAN PXE boot from ubuntu server"
date: 2011-09-06
forum: General Help
---

### Post by kamelie1706 on 2011-09-06
Hi,

I have a laptop toshiba 3110CT

I have a dd-wrt buffalo router acting as dhcp
```

IP=192.168.1.2
Additional DNSMasq Options
dhcp-boot=pxelinux.0,,192.168.1.194

```I have set my ubuntu server to serve boot image (IP=192.168.1.194)
I use atftp server: /etc/default/atftpd
```
USE_INETD=false
OPTIONS="--tftpd-timeout 300 --retry-timeout 5 --mcast-port 1758 --mcast-addr 239.239.239.0-255 --mcast-ttl 1 --maxthread 100 --verbose=5 --no-blksize --logfile=/var/log/atftp.log /srv/tftp"

```My /srv/tftp contains (standard netboot ubuntu 11.04)
```
boot.img     gtk       netboot         pxelinux.0    tinycore  ubuntu-installer
boot.img.gz  mini.iso  netboot.tar.gz  pxelinux.cfg  titi.txt  xen
```When I boot I got the following
```

Intel LANDesk Service Agent II version 0.99n
CLIENT IP 192.168.1.25
DHCP IP 192.168.1.194
GATEWAY IP 192.168.1.2

```... then timeout.

if I use tftp 192.168.1.194, I can get and transfer file normally

I have tried
```

echo 1 > /proc/sys/net/ipv4/ip_no_pmtu_dis
/etc/init.d/atftpd restart

```
do not solve ...

  Any idea where to look next? :confused:

---

### Post by ptmuldoon on 2011-09-08
hey kamelie.

I have a similar setup with dd-wrt router acting as the dhcp as well.

I followed this tutorial here using tftpd-hpa, and was able to network boot and install.  

[http://www.thelupine.com/content/ubuntu-pxe-booting](http://www.thelupine.com/content/ubuntu-pxe-booting)

Also, not sure if its necessary, but also include the name of your server in your dd-wrt DNSMasq setting.  Something like


dhcp-boot=pxelinux.0,SERVERNAME,192.168.1.194

---

### Post by kamelie1706 on 2011-09-08
thanks,

did you need to setup also dhcp on the image server in addition of your router?

I have not edited also the export file ...

---

### Post by ptmuldoon on 2011-09-09
No, i just used the dhcp off the router, and that guide got me pxe booting ubuntu with no issues.  Just skip over the dhcp info in the guide.

Although I am no trying to add pxe booting windows installs, and can't get it working.  I haven't found much on that yet.

---

### Post by Tweak42 on 2011-09-19
I also was successful in booting ubuntu via pxe setup with my tomato powered Linksys router doing the tftp hand off to a server.  Now I'm working on getting windows 7 added following a guide found here:  [http://www.ultimatedeployment.org/index.html](http://www.ultimatedeployment.org/index.html)

It's a bit more complicated because you have to boot into intermediate WinPE environment first before you can launch the Windows 7 setup.  It's the WinPE environment you would edit for say new network drivers, as opposed to just booting a newer linux distro that has had updated drivers complied in.

---

### Post by kamelie1706 on 2011-10-08
Now trying with tftpd-hpa .... 

/etc/default/tftpd-hpa
```
# /etc/default/tftpd-hpa
TFTP_USERNAME="tftp"
TFTP_DIRECTORY="/var/lib/tftpboot"
TFTP_ADDRESS="192.168.1.194:69"
TFTP_OPTIONS="--secure"

```From a terminal in the server
tftp
```
tftp> connect 
(to) 192.168.1.194
tftp> get pxelinux.0
Received 27202 bytes in 0.0 seconds

```

I have edited
```
/etc/exports
/var/lib/tftpboot/debian/squeeze/amd64 *(ro,sync,no_root_squash,no_subtree_check)

```

Router 
Additional DNSMasq Options
```
dhcp-boot=pxelinux.0,htpc,192.168.1.194
```So it seems that laptop get correct information, tftp server seems accessible ... but message still timeout
```
Intel LANDesk Service Agent II version 0.99n CLIENT IP 192.168.1.25 MASK 255.255.255.0 
DHCP IP 192.168.1.194 GATEWAY IP 192.168.1.2
TFTP .....
PXE-E32 TFTP OPEN TIMEOUT
PXE-M0F Exiting LANDesk

```:mad:
                                                                              
I have no other computer I could test pxe booting ...

---

### Post by Tweak42 on 2011-10-09
> **kamelie1706 said:**
> 
I have no other computer I could test pxe booting ...

Virtual Box can be configured to boot off PXE.

---

### Post by kamelie1706 on 2011-10-10
> **Tweak42 said:**
> Virtual Box can be configured to boot off PXE.

good idea ... will try that!

---

### Post by kamelie1706 on 2011-10-10
It seems problem is coming from the laptop ... I have no problem with virtualos machine
[https://picasaweb.google.com/lh/photo/VWzc6O9gLGMXAcbL5fYxJQ?feat=directlink](https://picasaweb.google.com/lh/photo/VWzc6O9gLGMXAcbL5fYxJQ?feat=directlink)

[IMG]https://picasaweb.google.com/lh/photo/VWzc6O9gLGMXAcbL5fYxJQ?feat=directlink[/IMG]

---

### Post by kamelie1706 on 2011-10-10
Do not get it according to this
[FONT=monospace]http://hreuver.home.xs4all.nl/pxelinux.txt
[/FONT]The PXE protocol uses a very complex set of extensions to DHCP or BOOTP.  However, most PXE implementations -- this includes all Intel ones version 0.99n and later -- seem to be able to boot in a "conventional" DHCP/TFTP configuration.  Assuming you don't have to support any very old or otherwise severely broken clients, this is probably the best configuration unless you already have a PXE boot server on your network.

I should not have any challenge ....

---

