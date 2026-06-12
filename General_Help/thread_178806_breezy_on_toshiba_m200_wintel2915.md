---
title: "breezy on toshiba m200 w/intel2915"
date: 2006-05-18
forum: General Help
---

### Post by mr.digwell on 2006-05-18
hi everyone
I hope someone can help me here cos i'm getting really frustrated! ](*,) 
I have just installed 5.10 on a toshiba portege m200, with intel 2915 wifi, using a network install (no bootable cd drive). Logging in to gnome brings up the error
   
  [B] 'The panel encountered a problem while loading
   "OAFIID:GNOME_Panel_WirelessApplet"[/B]
   do you want to delete the applet from your configuration?'
 
I don't know if this is related to my main problem of getting the card up & running.
I have tried ipw2200, ndiswrapper - no luck at all, & now back to ipw2200. 

  [B] ah@TwirlyTop:~$ iwconfig
   lo        no wireless extensions.

   eth1      no wireless extensions.

   sit0      no wireless extensions.[/B]

The card should be eth0.

   ah@TwirlyTop:~$ dmesg

   [4294670.209000] ACPI: Assum......
                         ........ ieee80211_crypt: registered algorithm 'NULL'
   [4294700.617000] ieee80211: 802.11 data/management/control stack, 1.1.13
   [4294700.617000] ieee80211: Copyright (C) 2004-2005 Intel Corporation     <jketreno@linux.intel.com>
   [4294700.877000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2dmprq
   [4294700.877000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
   [4294700.880000] ACPI: PCI Interrupt 0000:02:05.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[B]   [4294700.880000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection[4294701.706000] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
   [4294701.706000] ipw2200: Unable to load firmware: -2
   [4294701.706000] ipw2200: failed to register network device
   [4294701.720000] ACPI: PCI interrupt for device 0000:02:05.0 disabled
   [4294701.720000] ipw2200: probe of 0000:02:05.0 failed with error -5[/B]
   [4294701.802000] Linux Kernel Card Services
   [4294701.802000]   options:  [pci] [cardbus] [pm]
   [4294701.804000] PCI: Enabling device 0000:02:0b.0 (0000 -> 0002)
   [4294701.804000] ACPI: PCI Interru.......

I have already installed the firmware to /usr/lib/hotplug/firmware & also /lib/hotplug/firmware.
I have tried the workaround (which seems to work for quite a few people) but ubuntu wont let me edit the file

   [B]ah@TwirlyTop:~$ sudo echo 100 > /sys/class/firmware/timeout
   bash: /sys/class/firmware/timeout: Permission denied[/B]

Yet on forums it appears this method works for other ubuntu users.

can anyone help?

---

### Post by Ptero-4 on 2006-05-18
Are you using the user account that you created during the installation? Are you sure that the /etc/sudoers file contains the admin stuff? Are you sure that your user account is part of the group "admin"? If all three are correct sudo should work for you.

---

### Post by mr.digwell on 2006-05-18
sudo works for everything else, & the file permissions give root full rwx access.

---

