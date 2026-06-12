---
title: "Ati / flgrx driver issue"
date: 2011-02-01
forum: General Help
---

### Post by deviant on 2011-02-01
Hello good people, 

Recently I just installed 10.04.1 (x64) on a Acer Travelmate 6592 and got into several issues: 

1st - and foremost, as soon as I install the Ati/Amd proprietary driver I experience lots of black screen lockups, reboots, stripes and colored squares on the display, the display turning completely white and then the lock of the machine, the secondary display (external LCD) is not working properly & so on.
2nd - the computer is booting in console mode and I have to manually login and start the interface. It seems that there are some issues with the gdm not starting properly (have yet failed to log the error)

Next is the cut from syslog, exactly when I experienced one of the display issues: 
```
itch@Marvin:~$ tail -f /var/log/syslog 
Feb  1 20:02:10 Marvin avahi-daemon[935]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.141.
Feb  1 20:02:10 Marvin avahi-daemon[935]: New relevant interface wlan0.IPv4 for mDNS.
Feb  1 20:02:10 Marvin avahi-daemon[935]: Registering new address record for 10.0.0.141 on wlan0.IPv4.
Feb  1 20:02:11 Marvin NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Feb  1 20:02:11 Marvin NetworkManager: <info>  Policy set 'Auto rndsoft' (wlan0) as default for routing and DNS.
Feb  1 20:02:11 Marvin NetworkManager: <info>  Activation (wlan0) successful, device activated.
Feb  1 20:02:11 Marvin NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Feb  1 20:02:12 Marvin ntpdate[1697]: adjust time server 91.189.94.4 offset 0.068797 sec
Feb  1 20:02:17 Marvin kernel: [   67.942666] wlan0: no IPv6 routers present
Feb  1 20:02:48 Marvin AptDaemon: INFO: Initializing daemon
Feb  1 20:03:18 Marvin kernel: [  128.450392] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62
Feb  1 20:04:14 Marvin init: udevtrigger post-stop process (416) terminated with status 1
Feb  1 20:04:15 Marvin gdm-binary[1776]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  1 20:04:15 Marvin gdm-binary[1776]: WARNING: Unable to find users: no seat-id found
Feb  1 20:04:15 Marvin gdm-simple-slave[1784]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  1 20:04:15 Marvin gdm-binary[1776]: WARNING: GdmDisplay: display lasted 0.143563 seconds
Feb  1 20:04:15 Marvin gdm-simple-slave[1792]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  1 20:04:15 Marvin udevd[408]: worker [470] unexpectedly returned with status 0x0100
Feb  1 20:04:15 Marvin udevd[408]: worker [470] failed while handling '/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:33/IFX0102:00'
Feb  1 20:04:16 Marvin acpid: client connected from 1794[0:0]
Feb  1 20:04:16 Marvin acpid: 1 client rule loaded
Feb  1 20:04:17 Marvin kernel: [  187.216325] [fglrx:firegl_unlock] *ERROR* Process 1794 using kernel context 0
Feb  1 20:04:17 Marvin kernel: [  187.217403] Xorg:1794 conflicting memory types f0000000-f4000000 write-combining<->uncached-minus
Feb  1 20:04:17 Marvin kernel: [  187.217407] reserve_memtype failed 0xf0000000-0xf4000000, track write-combining, req uncached-minus
Feb  1 20:04:17 Marvin gdm-binary[1776]: WARNING: GdmDisplay: display lasted 2.200662 seconds
Feb  1 20:04:17 Marvin acpid: client 1410[0:0] has disconnected
Feb  1 20:04:17 Marvin acpid: client 1794[0:0] has disconnected
Feb  1 20:04:17 Marvin acpid: client connected from 1410[0:0]
Feb  1 20:04:17 Marvin acpid: 1 client rule loaded
Feb  1 20:04:17 Marvin gdm-simple-slave[1802]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  1 20:04:19 Marvin acpid: client 1410[0:0] has disconnected
Feb  1 20:04:19 Marvin acpid: client connected from 1804[0:0]
Feb  1 20:04:19 Marvin acpid: 1 client rule loaded
Feb  1 20:04:19 Marvin kernel: [  189.896531] [fglrx:firegl_unlock] *ERROR* Process 1804 using kernel context 0
Feb  1 20:04:19 Marvin kernel: [  189.897600] Xorg:1804 conflicting memory types f0000000-f4000000 write-combining<->uncached-minus
Feb  1 20:04:19 Marvin kernel: [  189.897603] reserve_memtype failed 0xf0000000-0xf4000000, track write-combining, req uncached-minus
Feb  1 20:04:20 Marvin gdm-binary[1776]: WARNING: GdmDisplay: display lasted 2.689246 seconds
Feb  1 20:04:20 Marvin acpid: client 1804[0:0] has disconnected
Feb  1 20:04:20 Marvin acpid: client connected from 1410[0:0]
Feb  1 20:04:20 Marvin acpid: 1 client rule loaded
Feb  1 20:04:20 Marvin gdm-simple-slave[1811]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  1 20:04:21 Marvin acpid: client 1410[0:0] has disconnected
Feb  1 20:04:21 Marvin acpid: client connected from 1813[0:0]
Feb  1 20:04:21 Marvin acpid: 1 client rule loaded
Feb  1 20:04:22 Marvin kernel: [  192.585793] [fglrx:firegl_unlock] *ERROR* Process 1813 using kernel context 0
Feb  1 20:04:22 Marvin kernel: [  192.586867] Xorg:1813 conflicting memory types f0000000-f4000000 write-combining<->uncached-minus
Feb  1 20:04:22 Marvin kernel: [  192.586870] reserve_memtype failed 0xf0000000-0xf4000000, track write-combining, req uncached-minus
Feb  1 20:04:22 Marvin gdm-binary[1776]: WARNING: GdmDisplay: display lasted 2.688816 seconds
Feb  1 20:04:22 Marvin acpid: client 1813[0:0] has disconnected
Feb  1 20:04:22 Marvin acpid: client connected from 1410[0:0]
Feb  1 20:04:22 Marvin acpid: 1 client rule loaded
Feb  1 20:04:22 Marvin gdm-simple-slave[1820]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  1 20:04:24 Marvin acpid: client 1410[0:0] has disconnected
Feb  1 20:04:24 Marvin acpid: client connected from 1822[0:0]
Feb  1 20:04:24 Marvin acpid: 1 client rule loaded
Feb  1 20:04:25 Marvin kernel: [  195.328382] [fglrx:firegl_unlock] *ERROR* Process 1822 using kernel context 0
Feb  1 20:04:25 Marvin kernel: [  195.329561] Xorg:1822 conflicting memory types f0000000-f4000000 write-combining<->uncached-minus
Feb  1 20:04:25 Marvin kernel: [  195.329565] reserve_memtype failed 0xf0000000-0xf4000000, track write-combining, req uncached-minus
Feb  1 20:04:25 Marvin acpid: client 1822[0:0] has disconnected
Feb  1 20:04:25 Marvin acpid: client connected from 1410[0:0]
Feb  1 20:04:25 Marvin acpid: 1 client rule loaded
Feb  1 20:04:25 Marvin gdm-binary[1776]: WARNING: GdmDisplay: display lasted 2.744318 seconds
Feb  1 20:04:25 Marvin gdm-simple-slave[1829]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  1 20:04:28 Marvin acpid: client 1410[0:0] has disconnected
Feb  1 20:04:28 Marvin acpid: client connected from 1831[0:0]
Feb  1 20:04:28 Marvin acpid: 1 client rule loaded
Feb  1 20:04:28 Marvin kernel: [  198.703609] [fglrx:firegl_unlock] *ERROR* Process 1831 using kernel context 0
Feb  1 20:04:28 Marvin kernel: [  198.704693] Xorg:1831 conflicting memory types f0000000-f4000000 write-combining<->uncached-minus
Feb  1 20:04:28 Marvin kernel: [  198.704696] reserve_memtype failed 0xf0000000-0xf4000000, track write-combining, req uncached-minus
Feb  1 20:04:28 Marvin acpid: client 1831[0:0] has disconnected
Feb  1 20:04:28 Marvin acpid: client connected from 1410[0:0]
Feb  1 20:04:28 Marvin acpid: 1 client rule loaded
Feb  1 20:04:28 Marvin gdm-simple-slave[1838]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Feb  1 20:04:30 Marvin acpid: client 1410[0:0] has disconnected
Feb  1 20:04:30 Marvin acpid: client connected from 1840[0:0]
Feb  1 20:04:30 Marvin acpid: 1 client rule loaded
Feb  1 20:04:31 Marvin kernel: [  201.409643] [fglrx:firegl_unlock] *ERROR* Process 1840 using kernel context 0
Feb  1 20:04:31 Marvin kernel: [  201.410746] Xorg:1840 conflicting memory types f0000000-f4000000 write-combining<->uncached-minus
Feb  1 20:04:31 Marvin kernel: [  201.410749] reserve_memtype failed 0xf0000000-0xf4000000, track write-combining, req uncached-minus
Feb  1 20:04:31 Marvin acpid: client 1840[0:0] has disconnected
Feb  1 20:04:31 Marvin acpid: client connected from 1410[0:0]
Feb  1 20:04:31 Marvin acpid: 1 client rule loaded
Feb  1 20:04:31 Marvin gdm-binary[1776]: WARNING: GdmDisplay: display lasted 2.717162 seconds
Feb  1 20:04:31 Marvin gdm-binary[1776]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Feb  1 20:04:31 Marvin init: gdm main process (1776) terminated with status 1
Feb  1 20:04:46 Marvin init: failsafe-x main process (1847) terminated with status 1
Feb  1 20:05:20 Marvin kernel: [  250.700289] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62
Feb  1 20:05:30 Marvin kernel: [  260.157672] lo: Disabled Privacy Extensions
Feb  1 20:07:21 Marvin kernel: [  371.450430] tpm_tis 00:0b: tpm_transmit: tpm_send: error -62
Feb  1 20:07:49 Marvin AptDaemon: INFO: Quiting due to inactivity
Feb  1 20:07:49 Marvin AptDaemon: INFO: Shutdown was requested
Feb  1 20:12:41 Marvin wpa_supplicant[1016]: WPA: Group rekeying completed with 00:1a:70:eb:a8:16 [GTK=TKIP]
Feb  1 20:12:41 Marvin NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> group handshake
Feb  1 20:12:41 Marvin NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Feb  1 20:15:59 Marvin bluetoothd[1039]: Discovery session 0x7f264aa40910 with :1.53 activated
Feb  1 20:17:01 Marvin CRON[2094]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
9
```

This is my dmesg | grep fglrx:
```
itch@Marvin:~$ dmesg  | grep fglrx
[    6.919417] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    6.974588] [fglrx] Maximum main memory to use for locked dma buffers: 1881 MBytes.
[    6.974885] [fglrx]   vendor: 1002 device: 94c8 count: 1
[    6.975335] [fglrx] ioport: bar 1, base 0x2000, size: 0x100
[    6.975553] [fglrx] Kernel PAT support is enabled
[    6.975577] [fglrx] module loaded - fglrx 8.72.11 [Apr  8 2010] with 1 minors
[   27.302259] fglrx_pci 0000:01:00.0: irq 32 for MSI/MSI-X
[   27.302887] [fglrx] Firegl kernel thread PID: 1414
[   27.303219] [fglrx] IRQ 32 Enabled
[   27.866344] [fglrx] Gart USWC size:626 M.
[   27.866347] [fglrx] Gart cacheable size:247 M.
[   27.866354] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   27.866356] [fglrx] Reserved FB block: Unshared offset:3e09000, size:1f7000 
[   27.866358] [fglrx] Reserved FB block: Unshared offset:fffc000, size:4000 
[  187.216325] [fglrx:firegl_unlock] *ERROR* Process 1794 using kernel context 0
[  189.896531] [fglrx:firegl_unlock] *ERROR* Process 1804 using kernel context 0
[  192.585793] [fglrx:firegl_unlock] *ERROR* Process 1813 using kernel context 0
[  195.328382] [fglrx:firegl_unlock] *ERROR* Process 1822 using kernel context 0
[  198.703609] [fglrx:firegl_unlock] *ERROR* Process 1831 using kernel context 0
[  201.409643] [fglrx:firegl_unlock] *ERROR* Process 1840 using kernel context 0

```

Currently running: 
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid
```

```
uname -a
Linux Marvin 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 23:42:43 UTC 2011 x86_64 GNU/Linux

```

I did try so search for solution using google / ubuntuforums.org but so far no solution. 

Is there any better alternative to the proprietary AMD driver?
I`m most concerned about the stability rather than 3D performance, though hardware accelerated decoding of videos will be a plus.

---

### Post by deviant on 2011-02-01
OK, new update: 

It seems that not only fglrx driver is causing me trouble, but also the open source one: as soon as I connect my secondary display the whole PC just crashes. 
Also, when I do get it to work (the external LCD), the display on it it`s all wobbly?

Tried to record syslog (via tail -f > log) but it did not help. As soon as my PC crashes, it seems that it`s not just the display but the whole. No logs where recorded :(

So, any tips / ideas on what might be causing this? And most important, how can I fix it?!

---

### Post by ste_bran on 2011-02-02
+1 on FGLRX not working for some Ati/AMD GPU. I activated the not open source driver. On reboot, after the ubuntu 10.10 boot screen, after the fourth dot turns red, I go to a black screen. I went into recovery and unistalled driver -- OK now. I am using AMD Raedon 6950 and 10.10 kernel 2.6.35-24. I am willing to post logs and help test, but since this is proprietary driver, not sure where to post anything.

Deviant, it sounds like you have unloaded the driver, so I think all we can do is ask/demand/wait for AMD to write linux driver. :mad: I assume the default driver is working for you, as it is for me.

---

### Post by cottfcfan on 2011-02-02
You may have already done this, but I find following this guide always works:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Download_the_latest_Catalyst_package).

Just remember to uninstall all existing drivers
```
sudo apt-get purge --remove fglrx*
```

---

