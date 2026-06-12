---
title: "VDR &amp; Tv Card timeout, can you help?"
date: 2012-06-02
forum: General Help
---

### Post by hopelessone on 2012-06-02
Hi Everyone,

This lasted from 10.10..now 12.04..

If I enable VDR, my card wont load, even if i delay it 500s!

Here is the logs with VDR disabled:
```
Jun  2 17:13:22 pangolin kernel: [   59.396035] tda1004x: timeout waiting for DSP ready
Jun  2 17:13:22 pangolin kernel: [   59.436023] tda1004x: found firmware revision 0 -- invalid
Jun  2 17:13:22 pangolin kernel: [   59.436027] tda1004x: waiting for firmware upload...
Jun  2 17:13:23 pangolin NetworkManager[994]: <info> DNS: starting dnsmasq...
Jun  2 17:13:23 pangolin dnsmasq[1984]: started, version 2.59 cache disabled
Jun  2 17:13:23 pangolin NetworkManager[994]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun  2 17:13:23 pangolin dnsmasq[1984]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun  2 17:13:23 pangolin dnsmasq[1984]: using nameserver 10.1.1.1#53
Jun  2 17:13:23 pangolin NetworkManager[994]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun  2 17:13:23 pangolin NetworkManager[994]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun  2 17:13:23 pangolin NetworkManager[994]: <info> Activation (eth0) successful, device activated.
Jun  2 17:13:23 pangolin NetworkManager[994]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  2 17:13:23 pangolin dbus[953]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun  2 17:13:23 pangolin dbus[953]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  2 17:13:29 pangolin kernel: [   66.592009] eth0: no IPv6 routers present
Jun  2 17:13:32 pangolin ntpdate[2122]: step time server 91.189.94.4 offset -0.652814 sec
Jun  2 17:13:34 pangolin kernel: [   71.976020] tda1004x: found firmware revision 29 -- ok
Jun  2 17:13:35 pangolin goa[2263]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun  2 17:13:38 pangolin NetworkManager[994]: <info> (eth0): IP6 addrconf timed out or failed.
```

And here it is enabled:
```
Jun  2 17:07:06 pangolin kernel: [   60.204025] tda1004x: found firmware revision 0 -- invalid
Jun  2 17:07:06 pangolin kernel: [   60.204029] tda1004x: waiting for firmware upload...
Jun  2 17:07:06 pangolin kernel: [   60.244042] tda1004x: found firmware revision 0 -- invalid
Jun  2 17:07:06 pangolin kernel: [   60.244046] tda1004x: trying to boot from eeprom
Jun  2 17:07:06 pangolin NetworkManager[997]: <info> DNS: starting dnsmasq...
Jun  2 17:07:06 pangolin dnsmasq[1876]: started, version 2.59 cache disabled
Jun  2 17:07:06 pangolin dnsmasq[1876]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
Jun  2 17:07:06 pangolin dnsmasq[1876]: using nameserver 10.1.1.1#53
Jun  2 17:07:06 pangolin NetworkManager[997]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun  2 17:07:06 pangolin NetworkManager[997]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun  2 17:07:07 pangolin NetworkManager[997]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jun  2 17:07:07 pangolin NetworkManager[997]: <info> Activation (eth0) successful, device activated.
Jun  2 17:07:07 pangolin NetworkManager[997]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun  2 17:07:07 pangolin dbus[950]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Jun  2 17:07:07 pangolin dbus[950]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Jun  2 17:07:08 pangolin kernel: [   62.580016] tda1004x: timeout waiting for DSP ready
Jun  2 17:07:08 pangolin kernel: [   62.660017] tda1004x: found firmware revision 0 -- invalid
Jun  2 17:07:08 pangolin kernel: [   62.660021] tda1004x: waiting for firmware upload...
Jun  2 17:07:13 pangolin kernel: [   67.392008] eth0: no IPv6 routers present
Jun  2 17:07:17 pangolin ntpdate[1951]: adjust time server 91.189.94.4 offset -0.310509 sec
Jun  2 17:07:20 pangolin goa[2059]: goa-daemon version 3.4.0 starting [main.c:112, main()]
Jun  2 17:07:22 pangolin NetworkManager[997]: <info> (eth0): IP6 addrconf timed out or failed.
Jun  2 17:07:22 pangolin NetworkManager[997]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun  2 17:07:22 pangolin NetworkManager[997]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun  2 17:07:22 pangolin NetworkManager[997]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun  2 17:07:32 pangolin kernel: [   86.568013] tda1004x: timeout waiting for DSP ready
Jun  2 17:07:32 pangolin kernel: [   86.648011] tda1004x: found firmware revision 0 -- invalid
Jun  2 17:07:32 pangolin kernel: [   86.648015] tda1004x: firmware upload failed
Jun  2 17:07:35 pangolin kernel: [   89.072011] tda1004x: timeout waiting for DSP ready
Jun  2 17:07:35 pangolin kernel: [   89.112019] tda1004x: found firmware revision 80 -- invalid
Jun  2 17:07:35 pangolin kernel: [   89.112022] tda1004x: firmware upload failed
Jun  2 17:07:35 pangolin vdr: [1539] frontend 0/0 provides DVB-T with QPSK,QAM16,QAM64 ("Philips TDA10046H DVB-T")
Jun  2 17:07:35 pangolin vdr: [2099] tuner on frontend 0/0 thread started (pid=1539, tid=2099)
```

Anyone know why this would be happening?

Here  is the VDR start up file:
```
# /etc/default/vdr
#
# See also /usr/share/doc/vdr/README.Debian.gz
#

# Change to 1 to enable vdr's init-script
ENABLED=0

# Change this to 1 if you want vdr to be able to shutdown the
# computer
ENABLE_SHUTDOWN=0

# Options that will be passed to vdr's commandline
# for example: OPTIONS="-w 15"
OPTIONS="-w 60"
```

Only works with ENABLED=0 and wait til ubuntu loads fully then sudo /etc/init.d/vdr start after editing the file and ENABLED=1 !!?

Tried OPTIONS="-w 60" right up to OPTIONS="-w 500" and same thing..tda1004x: firmware upload failed

I'm really stuck and thought you can help me fix this painful VDR problem I have..

[Edit] This seems to be a problem with sudo add-apt-repository ppa:bpl3f1lmootj/yavdr-unstable

If I use Ubuntu's no prob, BUT..ubuntu doesnt have the **[COLOR="Red"]vdr-plugin-xvdr[/COLOR]** I need so badly for XBMC to work..

Can anyone help with a working vdr-plugin-xvdr with ubuntus version?

---

