---
title: "Random Crashes"
date: 2011-05-24
forum: General Help
---

### Post by uShafee on 2011-05-24
Ubuntu keeps crashing on me at random once or twice per day. Everything just freezes and I have to hard reboot and lose all my work. This is really annoying. Can someone help me figure out what the issue is?

thanks.

---

### Post by 3Miro on 2011-05-24
- bad graphics driver
- bad specific program
- overheating

Those are some of the possibilities, so here are some questions:

- What is your hardware (video card specifically)? 
- What are you doing when it crashes?
- What programs do you have opened?
- Do you keep an eye on the temperature?

---

### Post by uShafee on 2011-05-24
- What is your hardware (video card specifically)? 
Its an ATI card (mobility radeon 5xxx series). i am using the proprietary drivers i downloaded from the amd website because i had problems with the default drivers. 

- What are you doing when it crashes?
I am normally surfing the web. The connection goes out before it crashes. maybe its the wireless card drivers fault? I also had trouble with the default drivers for the wireless card and had to install bcmwl-kernel-source (5.100.82.38) from synaptic. With the default drivers the network manager often does not detect available wireless networks.

- What programs do you have opened?
Most of the times its just google chrome

- Do you keep an eye on the temperature?
Yeah. the temperature is normal.

Thanks.

---

### Post by 3Miro on 2011-05-24
Downloading drivers from the web is the last resort solution for Linux. You should use Additional Drivers (search in the menu) also called "jockey". This is special program that lets you install drivers specially tweaked for your version of Ubuntu. It would be best to uninstall all drivers that you currently have and then use jockey to install them properly.

I don't know how to uninstall the ATI driver as I have no experience with those. Unfortunately this may be tricky. As is, it is possible for the driver to break on the next kernel update (this is one of the many advantages to using jockey).

Since the problem seems to be related to the wireless card, I would try fixing that one first. Uninstall the package from synaptic and then use jockey (you will probably need to connect to the internet with a cable).

---

### Post by NoNameWill on 2011-05-24
While you are at it. You should also test your RAM. Run a live cd and select Memtest. Have to hit enter right when the purple screen appears or it will load to the desktop.

---

### Post by uShafee on 2011-05-24
I have tried to use the drivers installed by jockey. but they just wont work. Rarely detects my wireless networks and sometimes i would plain lose connectivity and have to reboot 3 or 4 times before it would detect the networks again.

Also the jockey drivers for the graphics card makes my laptop heat up real bad. I have checked twice by uninstalling the drivers i downloaded from amd website and installing from jockey. the heatup issue starts as soon as i switch to jockey drivers.

---

### Post by 3Miro on 2011-05-24
> **uShafee said:**
> I have tried to use the drivers installed by jockey. but they just wont work. Rarely detects my wireless networks and sometimes i would plain lose connectivity and have to reboot 3 or 4 times before it would detect the networks again.

Also the jockey drivers for the graphics card makes my laptop heat up real bad. I have checked twice by uninstalling the drivers i downloaded from amd website and installing from jockey. the heatup issue starts as soon as i switch to jockey drivers.

Do the RAM test to make sure (boot from a LiveCD and run a memtest, make sure you are connected to power and keep an eye for overheating).

I am afraid the issue might be with the hardware. If the jockey drivers are that bad, then your laptop has hit some major incompatibility with Ubuntu and the jockey drivers as well as the ones from the web are closed and the Ubuntu community is not allowed to study and/or fix them. This happens with computers designed for Windows.

The only other thing that I can think of is to look on this forum and/or Google for people Linux and your exact laptop model.

---

### Post by linuxinstalledfromhdd on 2011-05-24
You can always roll back your version ubuntu to the previous version until you gain the stability you are looking for too.  Natty is cutting edge, and 10.10 has been more stable for me. Honestly I haven't had a crash on my system on my brand new laptop. It's a toshiba. Nothing super fancy.  Whenever I hear about crashes on Linux systems, it is usually due to some kind of driver issue, or old hardware.  Sometimes it's about compatibility.

---

### Post by uShafee on 2011-05-25
> **3Miro said:**
> Do the RAM test to make sure (boot from a LiveCD and run a memtest, make sure you are connected to power and keep an eye for overheating).

I am afraid the issue might be with the hardware. If the jockey drivers are that bad, then your laptop has hit some major incompatibility with Ubuntu and the jockey drivers as well as the ones from the web are closed and the Ubuntu community is not allowed to study and/or fix them. This happens with computers designed for Windows.

The only other thing that I can think of is to look on this forum and/or Google for people Linux and your exact laptop model.

I ran a mem test and everything seems okay. but my laptop did overheat a bit during the test. I have done a google search and this seems to be somewhat a common issue with people using broadcom cards. Thats how i installed the other drivers in the first place. 

> You can always roll back your version ubuntu to the previous version until you gain the stability you are looking for too. Natty is cutting edge, and 10.10 has been more stable for me. Honestly I haven't had a crash on my system on my brand new laptop. It's a toshiba. Nothing super fancy. Whenever I hear about crashes on Linux systems, it is usually due to some kind of driver issue, or old hardware. Sometimes it's about compatibility.

I cant really roll back because 10.10 is worse on my laptop regarding the driver issues. I couldnt get either the wireless card driver or the Ethernet driver to work. 

My hardware isnt that old. Core i3 processor, 4gb ram and an avg ati graphics card.

---

### Post by uShafee on 2011-05-25
irrelevant.

---

### Post by Antarctica32 on 2011-05-25
I find it hard to believe it has anything to do with the battery overheating. This sounds like something that happens often in windows and mac, but doesn't happen to often in linux. A program that is poorly written will ask the kernel for ram. The kernel keeps giving the program ram, but because the program is poorly written it just sucks up more and more ram for pointless stuff that is unnecessary. The thing is, most of the time the program is not one that is obvious when it is running. It doesn't have to be something like open office or chrome or fire fox. It could be an applet on a panel or an anti-virus scanner or some graphics thing. If this was windows i would say it is that, but it's not. A good way to test to see if this is it it to open the system monitor, i believe it is preinstalled. and then go to processes, and just look if anything is taking up an insane amount of ram. Also the program (if it even has something to do with a program) is probably one less commonly used, perhaps one from some random website you found. Also when did this start happening? If it has always been like this, it definitely has nothing to do with a program. In that case it probably has something to do with the whole driver thing you were talking about. 

Hope i could help

---

### Post by uShafee on 2011-05-25
so Ubuntu crashed again. :( I am attaching my system log and kernel log below. Crashed at 3.44AM

Just before crashing i have the following in my system log:
```

May 26 03:44:41 pc-name NetworkManager[886]: <info> monitoring kernel firmware directory '/lib/firmware'.
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: init!
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: update_system_hostname
May 26 03:44:41 pc-name NetworkManager[886]:    SCPluginIfupdown: management mode: unmanaged
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/wlan0, iface: wlan0)
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/eth0, iface: eth0)
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/eth0, iface: eth0): no ifupdown configuration found.
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: end _init.
May 26 03:44:41 pc-name NetworkManager[886]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
May 26 03:44:41 pc-name NetworkManager[886]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
May 26 03:44:41 pc-name NetworkManager[886]:    Ifupdown: get unmanaged devices count: 0
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: (154646560) ... get_connections.
May 26 03:44:41 pc-name NetworkManager[886]:    SCPlugin-Ifupdown: (154646560) ... get_connections (managed=false): return empty list.
May 26 03:44:41 pc-name kernel: [   20.069990] type=1400 audit(1306361681.358:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=976 comm="apparmor_parser"
May 26 03:44:41 pc-name kernel: [   20.071530] type=1400 audit(1306361681.362:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=978 comm="apparmor_parser"
May 26 03:44:41 pc-name kernel: [   20.072426] type=1400 audit(1306361681.362:13): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=978 comm="apparmor_parser"
May 26 03:44:41 pc-name kernel: [   20.075211] ppdev: user-space parallel port driver
May 26 03:44:41 pc-name kernel: [   20.075992] type=1400 audit(1306361681.366:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=976 comm="apparmor_parser"
May 26 03:44:41 pc-name NetworkManager[886]:    Ifupdown: get unmanaged devices count: 0
May 26 03:44:41 pc-name NetworkManager[886]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1c.1/0000:04:00.0/ieee80211/phy0/rfkill2) (driver <unknown>)
May 26 03:44:41 pc-name NetworkManager[886]: <info> found WiFi radio killswitch rfkill0 (at /sys/devices/platform/dell-laptop/rfkill/rfkill0) (driver dell-laptop)
May 26 03:44:41 pc-name gdm-binary[880]: WARNING: Unable to find users: no seat-id found
May 26 03:44:41 pc-name NetworkManager[886]: <info> WiFi enabled by radio killswitch; enabled by state file
May 26 03:44:41 pc-name NetworkManager[886]: <info> WWAN enabled by radio killswitch; enabled by state file
May 26 03:44:41 pc-name NetworkManager[886]: <info> WiMAX enabled by radio killswitch; enabled by state file
May 26 03:44:41 pc-name NetworkManager[886]: <info> Networking is enabled by state file
May 26 03:44:41 pc-name NetworkManager[886]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
May 26 03:44:41 pc-name NetworkManager[886]: <info> (wlan0): new 802.11 WiFi device (driver: 'brcm80211' ifindex: 3)
May 26 03:44:41 pc-name NetworkManager[886]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
May 26 03:44:41 pc-name NetworkManager[886]: <info> (wlan0): now managed
May 26 03:44:41 pc-name NetworkManager[886]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
May 26 03:44:41 pc-name NetworkManager[886]: <info> (wlan0): bringing up device.
May 26 03:44:41 pc-name NetworkManager[886]: <info> (wlan0): preparing device.
May 26 03:44:41 pc-name NetworkManager[886]: <info> (wlan0): deactivating device (reason: 2).
May 26 03:44:41 pc-name kernel: [   20.144264] ADDRCONF(NETDEV_UP): wlan0: link is not ready
May 26 03:44:41 pc-name NetworkManager[886]: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
May 26 03:44:41 pc-name NetworkManager[886]: <info> (eth0): carrier is OFF
May 26 03:44:41 pc-name NetworkManager[886]: <info> (eth0): new Ethernet device (driver: 'atl1c' ifindex: 2)
May 26 03:44:41 pc-name NetworkManager[886]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
May 26 03:44:41 pc-name NetworkManager[886]: <info> (eth0): now managed
May 26 03:44:41 pc-name NetworkManager[886]: <info> (eth0): device state change: 1 -> 2 (reason 2)
May 26 03:44:41 pc-name NetworkManager[886]: <info> (eth0): bringing up device.
May 26 03:44:44 pc-name kernel: [   22.454840] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
May 26 03:44:44 pc-name kernel: [   22.455046] atl1c 0000:05:00.0: irq 44 for MSI/MSI-X
May 26 03:44:45 pc-name kernel: [   23.732595] psmouse.c: resync failed, issuing reconnect request
May 26 03:44:45 pc-name kernel: [   23.814432] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 26 03:44:45 pc-name NetworkManager[886]: <info> (eth0): preparing device.
May 26 03:44:45 pc-name NetworkManager[886]: <info> (eth0): deactivating device (reason: 2).
May 26 03:44:45 pc-name NetworkManager[886]: <info> Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:1c.5/0000:05:00.0/net/eth0
May 26 03:44:45 pc-name NetworkManager[886]: <info> modem-manager is now available
May 26 03:44:45 pc-name NetworkManager[886]: <warn> bluez error getting default adapter: The name org.bluez was not provided by any .service files
May 26 03:44:45 pc-name NetworkManager[886]: <info> Trying to start the supplicant...
May 26 03:44:45 pc-name NetworkManager[886]: <info> (wlan0): supplicant manager state:  down -> idle
May 26 03:44:45 pc-name NetworkManager[886]: <info> (wlan0): device state change: 2 -> 3 (reason 0)

```

It looks like the connection did fail just before crashing. This is really starting to kill me. could somebody interpret the log for me and figure out what the problem is please please.

@Antarctica32 thanks for the input. yeh. but i dont think i have any unkonwn programs running.

[ Attachment: syslog]("http://maldiveshost.info/shafee/sys.log.txt")
[ Attachment: kernlog]("http://maldiveshost.info/shafee/kern.log.txt")

---

### Post by uShafee on 2011-05-26
bump

---

### Post by Antarctica32 on 2011-05-27
to tell you the truth i dont really know to much about this stuff. but i do know a few things that will help. did this just randomly start happening one day? how long ago was install? if you just installed would it be worth just re-installing? your hardware may have a problem with ubuntu. sometimes an install will just mess up one specific thing, for example i have seen several casses where after install someones ethernet just wont work. often a fresh install will fix these. another possiblity is that your hardware just isnt compatible with ubuntu. this is a lot less likely. i would say try booting froma live cd but that would take a while to see if it crashes. if you can, try booting froma live cd and see if it crashes. i would also try several different versions just to see what happens.

---

### Post by uShafee on 2011-05-28
its still crashing on me. Going to do a fresh install and will write back if this continues.

---

### Post by uShafee on 2011-05-31
thanks for all the help :)

seems like the drivers were not working well with only the 32bit installation. Changed over to 64bit and been smooth sailing there on. 

if you are on a dell 14R laptop and have issues, switch over to 64bit. Also turn off the wireless switch in BIOS if problems continue.

---

