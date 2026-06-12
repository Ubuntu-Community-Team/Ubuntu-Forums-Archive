---
title: "Wireless not currently an option and it ought to be"
date: 2010-03-01
forum: General Help
---

### Post by jamesisin on 2010-03-01
I built this machine (Dell Vectra with 9.10) for my brother and his wife to use as a media server.  For convenience (for them) I tossed in an old wireless card I had here.

While I was running the 244 updates for the new installation, something came up about there being a driver Ubuntu could install for the wireless card.  That seemed to succeed except it's not working.

I wasn't too concerned at the time thinking that the reboot which was inevitable would manage everything.  The reboot did change some things, but I have no wireless option.

Before the reboot wireless was enabled (but not working).  After the reboot enable wireless is greyed out.  I tried adding a wireless connection, but no matter what I put in the add connection dialog the Apply button remains greyed out.

I really don't know where to start.  Anybody up for some guidance?

---

### Post by efflandt on 2010-03-02
If the wireless device is a pci card, what does **sudo lspci -v** show for it?

If you go to System > Administration > Hardware Drivers (preferably with a temporary ethernet connection) do any possible drivers show up for it?  Some Broadcom devices like BCM4311 or BCM4312 use Broadcom STA (and/or bcmwl-kernel-source package) or some other Broadcom devices use Broadcom B43 (and/or b43-fwcutter package).

---

### Post by jamesisin on 2010-03-02
Thanks for taking a look.

According to Hardware Drivers I am currently using "Broadcom B43legacy wireless driver" and it mentions that "fwcutter is a tool which can extract firmware from various source files.It's written for BCM43xx driver files.).

Here is the relevant information from lspci:

```
02:0f.0 Network controller: Broadcom Corporation BCM4303 802.11b Wireless LAN Controller (rev 02)
	Subsystem: Linksys Device 4301
	Flags: bus master, fast devsel, latency 64, IRQ 5
	Memory at e8000000 (32-bit, non-prefetchable) [size=8K]
	Capabilities: [40] Power Management version 2
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
```

(If you want more output let me know.)

---

### Post by rnerwein on 2010-03-02
hi
try this ( may be helps you - run as root )
  ifconfig wlan0 up
  iwconfig wlan0 essid YourEssid key your_key mode Managed
  ifconfig wlan0 up
  dhcpcd -t 60
for wlan0 use your interface name.
ciao

---

### Post by jamesisin on 2010-03-02
I didn't get far:

```
sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132
```

And in case this is important:

```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

