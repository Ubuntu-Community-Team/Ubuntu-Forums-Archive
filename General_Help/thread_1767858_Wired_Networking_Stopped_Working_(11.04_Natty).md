---
title: "Wired Networking Stopped Working (11.04 Natty)"
date: 2011-05-26
forum: General Help
---

### Post by wraithrmm on 2011-05-26
Hi, I have been running Natty on my MacBook Pro for a while now and then suddenly while just using it normally (not installing etc), my skype crashed and would crash again on restart of the program. Now this could be a red herring, but though I'd include as much info as pos.

I installed all the updates the system told me to, to see if this would help and restarted.

On restart, the wired network would not connect. I get the following errors in my log:


May 26 12:46:40 richard-MacBookPro NetworkManager[763]: <info> Saved default wired connection 'Auto eth0' to persistent storage
May 26 12:46:41 richard-MacBookPro NetworkManager[763]:    keyfile: updating /etc/NetworkManager/system-connections/Auto eth0
May 26 12:46:41 richard-MacBookPro NetworkManager[763]:    Ifupdown: get unmanaged devices count: 0
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) starting connection 'Auto eth0'
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> (eth0): device state change: 3 -> 4 (reason 0)
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> (eth0): device state change: 4 -> 5 (reason 0)
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> (eth0): device state change: 5 -> 7 (reason 0)
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> dhclient started with pid 2112
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
May 26 12:46:41 richard-MacBookPro dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
May 26 12:46:41 richard-MacBookPro dhclient: Copyright 2004-2010 Internet Systems Consortium.
May 26 12:46:41 richard-MacBookPro dhclient: All rights reserved.
May 26 12:46:41 richard-MacBookPro dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
May 26 12:46:41 richard-MacBookPro dhclient: 
May 26 12:46:41 richard-MacBookPro NetworkManager[763]: <info> (eth0): DHCPv4 state changed nbi -> preinit
May 26 12:46:41 richard-MacBookPro dhclient: Listening on LPF/eth0/64:b9:e8:be:a7:38
May 26 12:46:41 richard-MacBookPro dhclient: Sending on   LPF/eth0/64:b9:e8:be:a7:38
May 26 12:46:41 richard-MacBookPro dhclient: Sending on   Socket/fallback
May 26 12:46:41 richard-MacBookPro dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 26 12:46:43 richard-MacBookPro dhclient: DHCPOFFER of 192.168.1.72 from 192.168.1.254
May 26 12:46:43 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 12:46:43 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 12:46:46 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 12:46:46 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 12:46:50 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 12:46:50 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 12:47:01 richard-MacBookPro dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 26 12:47:02 richard-MacBookPro dhclient: DHCPOFFER of 192.168.1.72 from 192.168.1.254
May 26 12:47:02 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 12:47:02 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 12:47:05 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 12:47:05 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 12:47:09 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 12:47:09 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 12:47:20 richard-MacBookPro dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
May 26 12:47:21 richard-MacBookPro dhclient: DHCPOFFER of 192.168.1.72 from 192.168.1.254
May 26 12:47:21 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 12:47:21 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 12:47:24 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 12:47:24 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <warn> (eth0): DHCPv4 request timed out.
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2112
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) started...
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <info> (eth0): device state change: 7 -> 9 (reason 5)
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <info> Marking connection 'Auto eth0' invalid.
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <warn> Activation (eth0) failed.
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Timeout) complete.
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <info> (eth0): device state change: 9 -> 3 (reason 0)
May 26 12:47:26 richard-MacBookPro NetworkManager[763]: <info> (eth0): deactivating device (reason: 0).
May 26 12:49:22 richard-MacBookPro kernel: [  981.698718] forcedeth 0000:00:0a.0: eth0: link down
May 26 12:49:22 richard-MacBookPro NetworkManager[763]: <info> (eth0): carrier now OFF (device state 3)
May 26 12:49:22 richard-MacBookPro NetworkManager[763]: <info> (eth0): device state change: 3 -> 2 (reason 40)
May 26 12:49:22 richard-MacBookPro NetworkManager[763]: <info> (eth0): deactivating device (reason: 40).
May 26 12:52:32 richard-MacBookPro NetworkManager[763]: <info> (eth0): carrier now ON (device state 2)
May 26 12:52:32 richard-MacBookPro NetworkManager[763]: <info> (eth0): device state change: 2 -> 3 (reason 40)
May 26 12:52:32 richard-MacBookPro kernel: [ 1172.197148] forcedeth 0000:00:0a.0: eth0: link up
May 26 12:52:36 richard-MacBookPro pommed[986]: Drive tray already open
May 26 12:53:22 richard-MacBookPro pommed[986]: last message repeated 40 times


ipconfig does not exist on my computer, otherwise I would echo this for you also.

I have not idea what has cause this so any help would be greatly recieved.

Thank you.

---

### Post by dandnsmith on 2011-05-26
It's **ifconfig** you need, not ipconfig (Windows equivalent) - as I'm always having to remind myself.

I'm intrigued by those DHCPNAK lines - its as if the offer is made, and then rescinded (for some, non-apparent reason), so you end up not getting the IP address, and so it doesn't allow you to continue sensibly.

I'm afraid I cannot think beyond that, as yet.

---

### Post by wraithrmm on 2011-05-26
Ok, right, doh! :-) My ifconfig output is as follows:

> eth0      Link encap:Ethernet  HWaddr 64:b9:e8:be:a7:38  
          inet6 addr: fe80::66b9:e8ff:febe:a738/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4876 (4.8 KB)  TX bytes:7359 (7.3 KB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14144 (14.1 KB)  TX bytes:14144 (14.1 KB)

Also, I foudn some more stuff that has reference to the NetworkManager in it from my syslog:

> May 26 15:12:02 richard-MacBookPro bluetoothd[849]: Listening for HCI events on hci0
May 26 15:12:02 richard-MacBookPro NetworkManager[713]: <warn> bluez error getting default adapter: No such adapter
May 26 15:12:02 richard-MacBookPro kernel: [   21.717169] input: Apple Inc. Apple Internal Keyboard / Trackpad as /devices/pci0000:00/0000:00:04.0/usb3/3-6/3-6:1.0/input/input8
May 26 15:12:02 richard-MacBookPro kernel: [   21.717337] apple 0003:05AC:0237.0002: input,hidraw3: USB HID v1.11 Keyboard [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input0
May 26 15:12:02 richard-MacBookPro kernel: [   21.719595] lirc_dev: IR Remote Control driver registered, major 249 
May 26 15:12:02 richard-MacBookPro kernel: [   21.721036] usb 4-1.2: USB disconnect, address 4
May 26 15:12:02 richard-MacBookPro kernel: [   21.721114] lirc_sir: module is from the staging directory, the quality is unknown, you have been warned.
May 26 15:12:02 richard-MacBookPro kernel: [   21.721701] lirc_register_driver: dev pointer not filled in!
May 26 15:12:02 richard-MacBookPro kernel: [   21.721704] lirc_sir: init_chrdev() failed.
May 26 15:12:02 richard-MacBookPro init: apport pre-start process (888) terminated with status 1
May 26 15:12:02 richard-MacBookPro bluetoothd[849]: HCI dev 0 up
May 26 15:12:02 richard-MacBookPro init: alsa-restore main process (896) terminated with status 19
May 26 15:12:02 richard-MacBookPro acpid: starting up with proc fs
May 26 15:12:02 richard-MacBookPro cron[899]: (CRON) INFO (pidfile fd = 3)
May 26 15:12:02 richard-MacBookPro acpid: 32 rules loaded
May 26 15:12:02 richard-MacBookPro acpid: waiting for events: event logging is off
May 26 15:12:02 richard-MacBookPro bluetoothd[849]: Adapter /org/bluez/839/hci0 has been enabled
May 26 15:12:02 richard-MacBookPro kernel: [   21.762980] Bluetooth: RFCOMM TTY layer initialized
May 26 15:12:02 richard-MacBookPro kernel: [   21.762985] Bluetooth: RFCOMM socket layer initialized
May 26 15:12:02 richard-MacBookPro kernel: [   21.762987] Bluetooth: RFCOMM ver 1.11
May 26 15:12:02 richard-MacBookPro init: apport post-stop process (941) terminated with status 1
May 26 15:12:02 richard-MacBookPro kernel: [   21.771846] apple 0003:05AC:0237.0003: hidraw4: USB HID v1.11 Device [Apple Inc. Apple Internal Keyboard / Trackpad] on usb-0000:00:04.0-6/input1
May 26 15:12:02 richard-MacBookPro kernel: [   21.829069] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
May 26 15:12:02 richard-MacBookPro kernel: [   21.829075] HDA Intel 0000:00:08.0: PCI INT A -> Link[LAZA] -> GSI 21 (level, low) -> IRQ 21
May 26 15:12:02 richard-MacBookPro kernel: [   21.829078] hda_intel: Disable MSI for Nvidia chipset
May 26 15:12:02 richard-MacBookPro kernel: [   21.829115] HDA Intel 0000:00:08.0: setting latency timer to 64
May 26 15:12:02 richard-MacBookPro kernel: [   21.931142] applesmc: key=300 fan=1 temp=14 acc=1 lux=2 kbd=1
May 26 15:12:02 richard-MacBookPro kernel: [   21.931145] applesmc: init_smcreg() took 50 ms
May 26 15:12:02 richard-MacBookPro kernel: [   21.940041] usb 4-1.3: USB disconnect, address 5
May 26 15:12:02 richard-MacBookPro kernel: [   22.012491] input: applesmc as /devices/platform/applesmc.768/input/input9
May 26 15:12:02 richard-MacBookPro kernel: [   22.013064] Registered led device: smc::kbd_backlight
May 26 15:12:02 richard-MacBookPro kernel: [   22.015076] nvidia_bl: MacBookPro 5,5 detected
May 26 15:12:02 richard-MacBookPro kernel: [   22.015285] nvidia_bl: Nvidia graphics adapter 10de:0863 (106b:00b9) detected
May 26 15:12:02 richard-MacBookPro anacron[980]: Anacron 2.3 started on 2011-05-26
May 26 15:12:02 richard-MacBookPro cron[982]: (CRON) STARTUP (fork ok)
May 26 15:12:02 richard-MacBookPro cron[982]: (CRON) INFO (Running @reboot jobs)
May 26 15:12:02 richard-MacBookPro pommed[985]: pommed v1.37 Apple laptops hotkeys handler
May 26 15:12:02 richard-MacBookPro pommed[985]: Copyright (C) 2006-2011 Julien BLACHE <jb@jblache.org>
May 26 15:12:02 richard-MacBookPro pommed[985]: DMI machine check: running on a MacBookPro5,5
May 26 15:12:02 richard-MacBookPro avahi-daemon[715]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::66b9:e8ff:febe:a738.
May 26 15:12:02 richard-MacBookPro avahi-daemon[715]: New relevant interface eth0.IPv6 for mDNS.
May 26 15:12:02 richard-MacBookPro avahi-daemon[715]: Registering new address record for fe80::66b9:e8ff:febe:a738 on eth0.*.
May 26 15:12:02 richard-MacBookPro kernel: [   22.436405] applesmc: light sensor data length set to 10
May 26 15:12:02 richard-MacBookPro pommed[985]: Found applesmc at /sys/class/hwmon/hwmon2/device
May 26 15:12:02 richard-MacBookPro pommed[985]: Dereferenced applesmc to /sys/devices/platform/applesmc.768
May 26 15:12:02 richard-MacBookPro anacron[980]: Normal exit (0 jobs run)
May 26 15:12:03 richard-MacBookPro pommed[985]: Audio initialization failed, audio support disabled
May 26 15:12:03 richard-MacBookPro noip2[1015]: v2.1.9 daemon started with NAT enabled
May 26 15:12:03 richard-MacBookPro noip2[1015]: Can't gethostbyname for dynupdate.no-ip.com
May 26 15:12:03 richard-MacBookPro noip2[1015]: Can't get our visible IP address from ip1.dynupdate.no-ip.com
May 26 15:12:03 richard-MacBookPro kernel: [   23.096894] vesafb: framebuffer at 0xd1000000, mapped to 0xf8f80000, using 1216k, total 1216k
May 26 15:12:03 richard-MacBookPro kernel: [   23.096898] vesafb: mode is 640x480x32, linelength=2560, pages=0
May 26 15:12:03 richard-MacBookPro kernel: [   23.096899] vesafb: scrolling: redraw
May 26 15:12:03 richard-MacBookPro kernel: [   23.096902] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
May 26 15:12:03 richard-MacBookPro kernel: [   23.097031] Console: switching to colour frame buffer device 80x30
May 26 15:12:03 richard-MacBookPro kernel: [   23.097043] fb0: VESA VGA frame buffer device
May 26 15:12:03 richard-MacBookPro dhclient: DHCPOFFER of 192.168.1.72 from 192.168.1.254
May 26 15:12:03 richard-MacBookPro dhclient: DHCPREQUEST of 192.168.1.72 on eth0 to 255.255.255.255 port 67
May 26 15:12:03 richard-MacBookPro dhclient: DHCPNAK from 192.168.1.254
May 26 15:12:03 richard-MacBookPro gdm-binary[1140]: WARNING: Unable to find users: no seat-id found

Hope some of this is of use, cos I've been trying all a can to get this going again. :-(

Thanks for the help! :-)

---

### Post by dandnsmith on 2011-05-26
Base on your later posting - the eth0 has an IP6 adress, but no IP4 Addr.
The router is offering IP4 addresses.
My next move would be to go to System|Preferences|Network Connections
Pick eth0 for editing
disable the IP6 on that tab
enable the IP4 for DHCP on that tab
exit, saving if prompted.
Reboot, and see if it is now working

---

### Post by wraithrmm on 2011-05-26
Thank for the advice, I gave this a try, but the IPv6 stuff was already set to 'Ignore'.

Is there anything else I can try?

---

### Post by dandnsmith on 2011-05-27
Have you managed to get an IP4 address showing up for eth0 on auto?
If not, why not try setting it to Manual and allocating one which could work - 192.168.1.72 possibly, or try something different like 192.168.1.100 if it won't let you have it, with netmask 255.255.255.0

Once obtained, you could then try meddling with the gateway and routing (if it isn't yet working).

---

