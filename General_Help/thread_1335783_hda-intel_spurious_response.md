---
title: "hda-intel: spurious response"
date: 2009-11-23
forum: General Help
---

### Post by W2IBC on 2009-11-23
wierd had a hard lockup min ago with 9.10 

reboot and find in the log this any ideas?

20:54:41 NSA-493587239 kernel: [   11.229977] HDA Intel 0000:80:01.0: PCI: Disallowing DAC for device
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429102] hda-intel: spurious response 0x1:0x0, last cmd=0x15f000e
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429109] hda-intel: spurious response 0x100018:0x0, last cmd=0x15f000e
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429113] hda-intel: spurious response 0x411:0x0, last cmd=0x15f000e
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429137] hda-intel: spurious response 0x411:0x0, last cmd=0x15f0200
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429183] hda_codec: invalid CONNECT_LIST verb 11[2]:0
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429222] hda-intel: spurious response 0x100311:0x0, last cmd=0x27f000e
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429281] hda-intel: spurious response 0x20010b:0x0, last cmd=0x27f000e
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429285] hda-intel: spurious response 0x300101:0x0, last cmd=0x27f000e
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429288] hda-intel: spurious response 0x30010d:0x0, last cmd=0x27f000e
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429305] hda_codec: invalid CONNECT_LIST verb 27[3]:0
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429325] hda-intel: spurious response 0x30010d:0x0, last cmd=0x27f0200
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429368] hda_codec: formats == 0 (nid=0x10, val=0x40010d, ovrd=1, streams=0x400101)
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429371] hda_codec: cannot attach PCM stream 0 for codec #0
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429408] hda_codec: formats == 0 (nid=0x14, val=0x400101, ovrd=1, streams=0x40010d)
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429410] hda_codec: cannot attach PCM stream 1 for codec #0
Nov 23 20:54:42 NSA-493587239 kernel: [   11.429798] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x1ff000c
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430065] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430068] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430095] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430098] hda-intel: spurious response 0x1:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430114] hda-intel: spurious response 0x18:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430135] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430156] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430218] hda-intel: spurious response 0x1:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430221] hda-intel: spurious response 0x21:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430224] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430241] hda-intel: spurious response 0x1:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430265] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430282] hda-intel: spurious response 0x5:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430302] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430323] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430344] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430365] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430385] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430409] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430471] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430474] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430477] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430490] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430510] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430532] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430552] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430573] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430641] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430644] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430647] hda-intel: spurious response 0x1c:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430678] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430682] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430697] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430718] hda-intel: spurious response 0x1c:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430738] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430804] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430807] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430809] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430822] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430844] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 kernel: [   11.430864] hda-intel: spurious response 0x0:0x0, last cmd=0x14f0d00
Nov 23 20:54:42 NSA-493587239 avahi-daemon[811]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Nov 23 20:54:42 NSA-493587239 avahi-daemon[811]: Successfully dropped root privileges.
Nov 23 20:54:42 NSA-493587239 avahi-daemon[811]: avahi-daemon 0.6.25 starting up.
Nov 23 20:54:42 NSA-493587239 avahi-daemon[811]: Successfully called chroot().
Nov 23 20:54:42 NSA-493587239 avahi-daemon[811]: Successfully dropped remaining capabilities.
Nov 23 20:54:42 NSA-493587239 avahi-daemon[811]: No service file found in /etc/avahi/services.
Nov 23 20:54:43 NSA-493587239 kernel: [   12.472121] type=1505 audit(1259027683.038:13): operation="profile_replace" pid=825 name=/usr/share/gdm/guest-session/Xsession
Nov 23 20:54:43 NSA-493587239 kernel: [   12.474905] type=1505 audit(1259027683.038:14): operation="profile_replace" pid=826 name=/sbin/dhclient3
Nov 23 20:54:43 NSA-493587239 kernel: [   12.475956] type=1505 audit(1259027683.038:15): operation="profile_replace" pid=826 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Nov 23 20:54:43 NSA-493587239 kernel: [   12.476501] type=1505 audit(1259027683.042:16): operation="profile_replace" pid=826 name=/usr/lib/connman/scripts/dhclient-script
Nov 23 20:54:43 NSA-493587239 kernel: [   12.483867] type=1505 audit(1259027683.046:17): operation="profile_replace" pid=827 name=/usr/bin/evince
Nov 23 20:54:43 NSA-493587239 kernel: [   12.498927] type=1505 audit(1259027683.062:18): operation="profile_replace" pid=827 name=/usr/bin/evince-previewer
Nov 23 20:54:43 NSA-493587239 kernel: [   12.507766] type=1505 audit(1259027683.070:19): operation="profile_replace" pid=827 name=/usr/bin/evince-thumbnailer
Nov 23 20:54:43 NSA-493587239 kernel: [   12.520564] type=1505 audit(1259027683.086:20): operation="profile_replace" pid=829 name=/usr/lib/cups/backend/cups-pdf
Nov 23 20:54:43 NSA-493587239 kernel: [   12.521731] type=1505 audit(1259027683.086:21): operation="profile_replace" pid=829 name=/usr/sbin/cupsd
Nov 23 20:54:43 NSA-493587239 NetworkManager: <info>  starting...
Nov 23 20:54:43 NSA-493587239 avahi-daemon[811]: Network interface enumeration completed.
Nov 23 20:54:43 NSA-493587239 avahi-daemon[811]: Registering HINFO record with values 'I686'/'LINUX'.
Nov 23 20:54:43 NSA-493587239 avahi-daemon[811]: Server startup complete. Host name is NSA-493587239.local. Local service cookie is 3714714326.
Nov 23 20:54:43 NSA-493587239 kernel: [   12.690464] type=1505 audit(1259027683.254:22): operation="profile_replace" pid=830 name=/usr/sbin/mysqld
Nov 23 20:54:43 NSA-493587239 NetworkManager: <info>  Trying to start the modem-manager...
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322021] hda-intel: spurious response 0x1:0x0, last cmd=0x17b2001
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322183] hda-intel: spurious response 0x100311:0x0, last cmd=0x20b8000
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322622] hda-intel: spurious response 0x10140f0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322642] hda-intel: spurious response 0x22140ff:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322663] hda-intel: spurious response 0x2a19038:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322683] hda-intel: spurious response 0x410160f1:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322704] hda-intel: spurious response 0x410120f4:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322725] hda-intel: spurious response 0x99370137:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322746] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322767] hda-intel: spurious response 0x47c421f0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322788] hda-intel: spurious response 0x10191349:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322809] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322829] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322850] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322871] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322892] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322918] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322934] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322955] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322975] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.322996] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323017] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323038] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323059] hda-intel: spurious response 0x1:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323080] hda-intel: spurious response 0x18:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323100] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323121] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323142] hda-intel: spurious response 0x1:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323163] hda-intel: spurious response 0x21:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323183] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323204] hda-intel: spurious response 0x1:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323225] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323246] hda-intel: spurious response 0x5:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323267] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323287] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323308] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323329] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323350] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323371] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323392] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323413] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323433] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323454] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323475] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323496] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323517] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323538] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323559] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323580] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323606] hda-intel: spurious response 0x1c:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323622] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323642] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323663] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323684] hda-intel: spurious response 0x1c:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323705] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323725] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323746] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323767] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323787] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323808] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323829] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323850] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323871] hda-intel: spurious response 0x80061f17:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323892] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323913] hda-intel: spurious response 0x80061400:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323933] hda-intel: spurious response 0x80061400:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323954] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323975] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.323996] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324017] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324038] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324058] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324093] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324123] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324127] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324145] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324162] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324183] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324203] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324224] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324245] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324266] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324292] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324307] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324328] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324349] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324369] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324390] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324411] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324432] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324453] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324474] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324495] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324515] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324536] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324557] hda-intel: spurious response 0x17:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324578] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:43 NSA-493587239 kernel: [   13.324599] hda-intel: spurious response 0x0:0x0, last cmd=0x1370600
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Novatel
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin MotoC
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Sierra
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Option High-Speed
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Gobi
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin ZTE
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Generic
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Nokia
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Huawei
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Ericsson MBM
Nov 23 20:54:44 NSA-493587239 modem-manager: Loaded plugin Option
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615326] hda-intel: spurious response 0x11061708:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615343] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615363] hda-intel: spurious response 0x100700:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615425] hda-intel: spurious response 0x100018:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615446] hda-intel: spurious response 0x411:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615467] hda-intel: spurious response 0x411:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615488] hda-intel: spurious response 0x411:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615509] hda-intel: spurious response 0x411:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615530] hda-intel: spurious response 0x211:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615551] hda-intel: spurious response 0x10051b:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615572] hda-intel: spurious response 0x100311:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615592] hda-intel: spurious response 0x20010b:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615613] hda-intel: spurious response 0x300101:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615634] hda-intel: spurious response 0x30010d:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615655] hda-intel: spurious response 0x30010d:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615676] hda-intel: spurious response 0x30010d:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615697] hda-intel: spurious response 0x40010d:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615717] hda-intel: spurious response 0x400101:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615738] hda-intel: spurious response 0x400101:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615759] hda-intel: spurious response 0x40010d:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615780] hda-intel: spurious response 0x40010d:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615801] hda-intel: spurious response 0x400101:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615821] hda-intel: spurious response 0x400101:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615842] hda-intel: spurious response 0x400101:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615863] hda-intel: spurious response 0x400001:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615884] hda-intel: spurious response 0x400301:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615905] hda-intel: spurious response 0x400201:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615926] hda-intel: spurious response 0x10051b:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615947] hda-intel: spurious response 0x410110f2:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615968] hda-intel: spurious response 0x1a19036:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.615988] hda-intel: spurious response 0x181303e:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616020] hda-intel: spurious response 0x10140f0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616030] hda-intel: spurious response 0x22140ff:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616050] hda-intel: spurious response 0x2a19038:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616071] hda-intel: spurious response 0x410160f1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616093] hda-intel: spurious response 0x410120f4:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616113] hda-intel: spurious response 0x99370137:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616134] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616155] hda-intel: spurious response 0x47c421f0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616175] hda-intel: spurious response 0x10191349:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616195] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616216] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616237] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616258] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616279] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616300] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616320] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616341] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616362] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616383] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616404] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616425] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616446] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616467] hda-intel: spurious response 0x18:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616487] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616508] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616529] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616549] hda-intel: spurious response 0x21:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616570] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616591] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616612] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616632] hda-intel: spurious response 0x5:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616653] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616674] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616695] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616716] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616737] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616758] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616778] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616799] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616820] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616841] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616862] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616882] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616903] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616924] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616945] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616965] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.616987] hda-intel: spurious response 0x1c:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617007] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617028] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617049] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617070] hda-intel: spurious response 0x1c:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617090] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617111] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617132] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617153] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617174] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617195] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617216] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617236] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617257] hda-intel: spurious response 0x80061f17:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617278] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617299] hda-intel: spurious response 0x80061400:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617320] hda-intel: spurious response 0x80061400:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617340] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617361] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617382] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617403] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617423] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617445] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617465] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617486] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617507] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617528] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617548] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617569] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617590] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617611] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617632] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617653] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617674] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617694] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617715] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617736] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617757] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617778] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617798] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617819] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617840] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617861] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617881] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617902] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617923] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617944] hda-intel: spurious response 0x17:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617965] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.617986] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618006] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618027] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618048] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618069] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618090] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618111] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618131] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618152] hda-intel: spurious response 0x17:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618173] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618194] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618214] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618235] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618256] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618277] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618298] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618319] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618339] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618360] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618381] hda-intel: spurious response 0x1:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618402] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.618423] hda-intel: spurious response 0x0:0x0, last cmd=0x2039013
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651761] hda-intel: spurious response 0x11061708:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651778] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651798] hda-intel: spurious response 0x100700:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651819] hda-intel: spurious response 0x10001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651840] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651860] hda-intel: spurious response 0x100018:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651882] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651903] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651923] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651944] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651965] hda-intel: spurious response 0x211:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.651986] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652029] hda-intel: spurious response 0x100311:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652033] hda-intel: spurious response 0x20010b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652052] hda-intel: spurious response 0x300101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652073] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652094] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652114] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652135] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652156] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652177] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652198] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652218] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652239] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652259] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652280] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652301] hda-intel: spurious response 0x400001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652322] hda-intel: spurious response 0x400301:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652343] hda-intel: spurious response 0x400201:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652364] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652385] hda-intel: spurious response 0x410110f2:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652406] hda-intel: spurious response 0x1a19036:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652426] hda-intel: spurious response 0x181303e:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652447] hda-intel: spurious response 0x10140f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652468] hda-intel: spurious response 0x22140ff:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652489] hda-intel: spurious response 0x2a19038:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652510] hda-intel: spurious response 0x410160f1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652531] hda-intel: spurious response 0x410120f4:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652552] hda-intel: spurious response 0x99370137:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652572] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652592] hda-intel: spurious response 0x47c421f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652614] hda-intel: spurious response 0x10191349:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652634] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652655] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652686] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652703] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652718] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652739] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652759] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652780] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652801] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652822] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652843] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652864] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652884] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652905] hda-intel: spurious response 0x18:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652926] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652946] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652967] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.652988] hda-intel: spurious response 0x21:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653009] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653030] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653050] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653071] hda-intel: spurious response 0x5:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653092] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653113] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653134] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653155] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653175] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653196] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653217] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653238] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653259] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653280] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653301] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653321] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653342] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653363] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653383] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653405] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653425] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653446] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653467] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653487] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653508] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653529] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653550] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653571] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653592] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653613] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653633] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653654] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653675] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653696] hda-intel: spurious response 0x80061f17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653717] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653738] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653758] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653779] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653800] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653821] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653841] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653862] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653883] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653904] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653925] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653946] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653966] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.653987] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654008] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654029] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654050] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654071] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654092] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654112] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654133] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654154] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654175] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654195] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654216] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654237] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654258] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654279] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654299] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654320] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654341] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654362] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654383] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654403] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654424] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654445] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654466] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654487] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654508] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654529] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654550] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654570] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654591] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654612] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654632] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654653] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654674] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654695] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654716] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654736] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654757] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654778] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654799] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654820] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654841] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654861] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.654882] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723037] hda-intel: spurious response 0x11061708:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723053] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723074] hda-intel: spurious response 0x100700:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723094] hda-intel: spurious response 0x10001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723115] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723135] hda-intel: spurious response 0x100018:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723157] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723177] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723199] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723220] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723239] hda-intel: spurious response 0x211:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723261] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723282] hda-intel: spurious response 0x100311:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723303] hda-intel: spurious response 0x20010b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723324] hda-intel: spurious response 0x300101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723345] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723365] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723385] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723406] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723427] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723448] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723469] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723489] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723510] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723531] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723551] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723573] hda-intel: spurious response 0x400001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723593] hda-intel: spurious response 0x400301:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723614] hda-intel: spurious response 0x400201:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723635] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723656] hda-intel: spurious response 0x410110f2:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723677] hda-intel: spurious response 0x1a19036:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723697] hda-intel: spurious response 0x181303e:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723718] hda-intel: spurious response 0x10140f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723739] hda-intel: spurious response 0x22140ff:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723760] hda-intel: spurious response 0x2a19038:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723781] hda-intel: spurious response 0x410160f1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723803] hda-intel: spurious response 0x410120f4:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723823] hda-intel: spurious response 0x99370137:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723843] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723865] hda-intel: spurious response 0x47c421f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723885] hda-intel: spurious response 0x10191349:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723906] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723927] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723947] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723970] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.723991] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724026] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724057] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724061] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724081] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724098] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724119] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724147] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724159] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724183] hda-intel: spurious response 0x18:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724201] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724222] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724242] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724264] hda-intel: spurious response 0x21:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724285] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724305] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724325] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724346] hda-intel: spurious response 0x5:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724368] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724388] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724409] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724430] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724450] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724471] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724492] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724513] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724534] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724555] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724577] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724597] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724617] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724638] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724659] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724681] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724702] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724723] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724743] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724763] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724791] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724808] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724826] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724846] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724867] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724888] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724908] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724929] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724950] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724971] hda-intel: spurious response 0x80061f17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.724992] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725014] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725034] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725055] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725076] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725097] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725118] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725139] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725165] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725180] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725202] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725221] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725242] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725262] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725283] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725304] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725326] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725348] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725366] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725389] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725408] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725430] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725451] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725471] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725493] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725513] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725532] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725554] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725575] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725595] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725617] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725637] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725658] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725678] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725702] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725722] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725742] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725762] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725784] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725805] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725825] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725845] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725869] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725888] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725909] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725928] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725952] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725971] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.725991] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726012] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726033] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726053] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726077] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726097] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726116] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726136] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726158] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726179] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726199] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726221] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726241] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.726261] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865066] hda-intel: spurious response 0x11061708:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865082] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865103] hda-intel: spurious response 0x100700:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865124] hda-intel: spurious response 0x10001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865146] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865165] hda-intel: spurious response 0x100018:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865186] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865207] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865228] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865248] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865269] hda-intel: spurious response 0x211:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865291] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865311] hda-intel: spurious response 0x100311:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865331] hda-intel: spurious response 0x20010b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865353] hda-intel: spurious response 0x300101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865373] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865395] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865415] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865435] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865457] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865477] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865498] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865518] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865550] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865560] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865586] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865654] hda-intel: spurious response 0x400001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865657] hda-intel: spurious response 0x400301:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865660] hda-intel: spurious response 0x400201:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865687] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865691] hda-intel: spurious response 0x410110f2:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865706] hda-intel: spurious response 0x1a19036:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865728] hda-intel: spurious response 0x181303e:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865748] hda-intel: spurious response 0x10140f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865768] hda-intel: spurious response 0x22140ff:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865789] hda-intel: spurious response 0x2a19038:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865811] hda-intel: spurious response 0x410160f1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865831] hda-intel: spurious response 0x410120f4:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865852] hda-intel: spurious response 0x99370137:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865873] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865893] hda-intel: spurious response 0x47c421f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865914] hda-intel: spurious response 0x10191349:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865935] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865958] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865977] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.865999] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866018] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866039] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866061] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866081] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866102] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866122] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866143] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866165] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866186] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866206] hda-intel: spurious response 0x18:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866226] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866247] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866268] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866289] hda-intel: spurious response 0x21:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866312] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866331] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866352] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866373] hda-intel: spurious response 0x5:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866393] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866414] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866434] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866456] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866476] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866497] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866522] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866539] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866560] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866581] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866603] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866627] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866644] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866664] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866685] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866705] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866726] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866747] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866768] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866789] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866810] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866831] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866851] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866871] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866892] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866914] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866935] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866957] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.866982] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867000] hda-intel: spurious response 0x80061f17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867021] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867041] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867062] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867084] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867104] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867125] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867147] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867166] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867187] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867208] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867229] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867250] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867271] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867292] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867312] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867333] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867354] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867375] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867396] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867417] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867437] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867458] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867479] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867499] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867520] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867541] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867562] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867583] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867604] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867625] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867645] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867666] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867687] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867708] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867729] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867750] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867771] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867791] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867812] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867833] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867854] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867875] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867896] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867916] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867937] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867958] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.867979] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868000] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868045] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868049] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868062] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868086] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868104] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868125] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868145] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868166] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868187] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868208] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868228] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868249] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868270] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868290] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868311] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868332] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868353] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868374] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868394] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868416] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868437] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868457] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868478] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868499] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868520] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868540] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868561] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868582] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.868603] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992407] hda-intel: spurious response 0x11061708:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992421] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992443] hda-intel: spurious response 0x100700:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992463] hda-intel: spurious response 0x10001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992485] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992505] hda-intel: spurious response 0x100018:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992526] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992547] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992567] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992588] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992609] hda-intel: spurious response 0x211:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992630] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992651] hda-intel: spurious response 0x100311:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992672] hda-intel: spurious response 0x20010b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992693] hda-intel: spurious response 0x300101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992713] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992734] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992755] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992776] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992796] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992817] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992838] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992859] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992879] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992900] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992921] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992942] hda-intel: spurious response 0x400001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992962] hda-intel: spurious response 0x400301:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.992984] hda-intel: spurious response 0x400201:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993005] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993025] hda-intel: spurious response 0x410110f2:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993047] hda-intel: spurious response 0x1a19036:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993067] hda-intel: spurious response 0x181303e:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993088] hda-intel: spurious response 0x10140f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993108] hda-intel: spurious response 0x22140ff:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993129] hda-intel: spurious response 0x2a19038:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993153] hda-intel: spurious response 0x410160f1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993171] hda-intel: spurious response 0x410120f4:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993192] hda-intel: spurious response 0x99370137:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993212] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993234] hda-intel: spurious response 0x47c421f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993267] hda-intel: spurious response 0x10191349:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993335] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993339] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993341] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993344] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993358] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993381] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993400] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993423] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993443] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993464] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993485] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993506] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993526] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993547] hda-intel: spurious response 0x18:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993568] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993589] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993610] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993631] hda-intel: spurious response 0x21:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993651] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993672] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993693] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993714] hda-intel: spurious response 0x5:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993735] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993756] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993777] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993797] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993818] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993839] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993860] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993880] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993902] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993922] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993943] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993964] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.993984] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994005] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994026] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994047] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994068] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994089] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994110] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994130] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994151] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994172] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994193] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994214] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994235] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994255] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994276] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994297] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994318] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994340] hda-intel: spurious response 0x80061f17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994360] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994381] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994401] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994422] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994443] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994464] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994485] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994506] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994527] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994548] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994568] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994589] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994610] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994631] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994651] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994672] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994693] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994714] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994735] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994755] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994776] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994798] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994818] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994839] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994860] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994880] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994901] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994922] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994943] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994964] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.994985] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995006] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995026] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995047] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995068] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995089] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995110] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995131] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995152] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995172] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995193] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995214] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995235] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995256] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995277] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995297] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995318] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995339] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995360] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995381] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995402] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995422] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995444] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995464] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995485] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995506] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995527] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995547] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995568] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995590] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995610] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995631] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995651] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995672] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995693] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995714] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995736] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995756] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995776] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995797] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995819] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995839] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995860] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995881] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995902] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995923] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995943] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995964] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.995985] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.996025] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.996029] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.996047] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.996069] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.996088] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.996110] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   13.996130] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060845] hda-intel: spurious response 0x11061708:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060852] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060862] hda-intel: spurious response 0x100700:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060884] hda-intel: spurious response 0x10001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060905] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060926] hda-intel: spurious response 0x100018:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060948] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060968] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.060989] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061010] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061031] hda-intel: spurious response 0x211:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061051] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061073] hda-intel: spurious response 0x100311:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061094] hda-intel: spurious response 0x20010b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061159] hda-intel: spurious response 0x300101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061162] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061165] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061176] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061196] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061217] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061239] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061259] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061280] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061301] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061322] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061342] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061364] hda-intel: spurious response 0x400001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061384] hda-intel: spurious response 0x400301:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061404] hda-intel: spurious response 0x400201:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061430] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061446] hda-intel: spurious response 0x410110f2:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061468] hda-intel: spurious response 0x1a19036:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061489] hda-intel: spurious response 0x181303e:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061511] hda-intel: spurious response 0x10140f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061572] hda-intel: spurious response 0x22140ff:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061575] hda-intel: spurious response 0x2a19038:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061579] hda-intel: spurious response 0x410160f1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061592] hda-intel: spurious response 0x410120f4:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061613] hda-intel: spurious response 0x99370137:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061634] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061655] hda-intel: spurious response 0x47c421f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061676] hda-intel: spurious response 0x10191349:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061695] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061719] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061737] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061758] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061779] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061801] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061822] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061842] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061863] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061883] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061904] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061925] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061954] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061966] hda-intel: spurious response 0x18:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.061988] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062008] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062028] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062050] hda-intel: spurious response 0x21:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062070] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062091] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062112] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062133] hda-intel: spurious response 0x5:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062154] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062174] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062198] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062219] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062245] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062312] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062315] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062318] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062343] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062346] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062363] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062384] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062405] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062426] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062447] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062467] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062488] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062508] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062530] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062551] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062572] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062592] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062613] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062633] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062654] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062675] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062696] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062717] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062738] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062759] hda-intel: spurious response 0x80061f17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062779] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062800] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062821] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062842] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062863] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062884] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062905] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062925] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062946] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062967] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.062988] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063009] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063030] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063051] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063071] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063092] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063112] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063134] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063154] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063176] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063196] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063217] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063238] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063258] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063279] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063300] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063321] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063342] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063363] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063383] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063404] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063426] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063446] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063467] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063488] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063509] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063529] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063551] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063571] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063592] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063613] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063634] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063655] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063676] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063696] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063717] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063738] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063759] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063780] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063803] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063822] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063842] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063863] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063884] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063904] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063925] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063946] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063967] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.063987] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064030] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064033] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064050] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064071] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064092] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064113] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064134] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064154] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064175] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064196] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064218] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064242] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064259] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064279] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064299] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064320] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064341] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064362] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064383] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064404] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064425] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064446] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064466] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064489] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064509] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064529] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064550] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064571] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064592] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064612] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064633] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064653] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064675] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.064697] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097180] hda-intel: spurious response 0x11061708:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097196] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097217] hda-intel: spurious response 0x100700:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097238] hda-intel: spurious response 0x10001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097258] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097279] hda-intel: spurious response 0x100018:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097301] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097321] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097342] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097363] hda-intel: spurious response 0x411:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097384] hda-intel: spurious response 0x211:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097404] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097425] hda-intel: spurious response 0x100311:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097446] hda-intel: spurious response 0x20010b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097467] hda-intel: spurious response 0x300101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097487] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097508] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097529] hda-intel: spurious response 0x30010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097550] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097571] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097592] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097612] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097633] hda-intel: spurious response 0x40010d:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097654] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097675] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097696] hda-intel: spurious response 0x400101:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097717] hda-intel: spurious response 0x400001:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097738] hda-intel: spurious response 0x400301:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097758] hda-intel: spurious response 0x400201:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097780] hda-intel: spurious response 0x10051b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097800] hda-intel: spurious response 0x410110f2:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097820] hda-intel: spurious response 0x1a19036:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097841] hda-intel: spurious response 0x181303e:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097862] hda-intel: spurious response 0x10140f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097883] hda-intel: spurious response 0x22140ff:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097904] hda-intel: spurious response 0x2a19038:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097925] hda-intel: spurious response 0x410160f1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097946] hda-intel: spurious response 0x410120f4:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097966] hda-intel: spurious response 0x99370137:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.097987] hda-intel: spurious response 0x74461f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098008] hda-intel: spurious response 0x47c421f0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098029] hda-intel: spurious response 0x10191349:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098050] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098071] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098091] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098112] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098133] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098153] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098174] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098195] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098216] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098237] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098257] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098278] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098300] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098321] hda-intel: spurious response 0x18:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098341] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098362] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098383] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098403] hda-intel: spurious response 0x21:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098424] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098445] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098466] hda-intel: spurious response 0xa07e0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098486] hda-intel: spurious response 0x5:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098507] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098529] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098549] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098569] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098590] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098612] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098633] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098653] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098674] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098695] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098715] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098736] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098757] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098778] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098799] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098820] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098841] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098861] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098882] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098903] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098924] hda-intel: spurious response 0x1c:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098944] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098965] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.098986] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099007] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099028] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099049] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099069] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099090] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099111] hda-intel: spurious response 0x80061f17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099132] hda-intel: spurious response 0x80061b1b:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099153] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099173] hda-intel: spurious response 0x80061400:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099194] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099215] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099236] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099257] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099278] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099299] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099319] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099340] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099361] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099381] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099402] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099423] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099444] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099465] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099486] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099506] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099527] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099548] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099569] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099590] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099611] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099631] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099652] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099673] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099694] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099715] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099735] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099756] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099777] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099798] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099819] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099839] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099860] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099881] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099902] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099923] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099943] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099965] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.099985] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100018] hda-intel: spurious response 0x17:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100031] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100052] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100073] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100093] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100114] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100135] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100156] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100177] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100198] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100218] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100240] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100260] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100281] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100307] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100322] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100348] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100416] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100420] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100423] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100448] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100451] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100468] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100489] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100510] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100532] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100551] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100572] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100593] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100614] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100635] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100655] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100676] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100697] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100717] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100738] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100759] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100780] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100801] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100822] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100843] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100863] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100884] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100905] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100926] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100947] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100967] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.100989] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.101009] hda-intel: spurious response 0x0:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.101031] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.101050] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.101071] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.101092] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 kernel: [   14.101113] hda-intel: spurious response 0x1:0x0, last cmd=0x20f0100
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: init!
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:09.0/net/wlan0, iface: wlan0)
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:09.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0)
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:12.0/net/eth0, iface: eth0): no ifupdown configuration found.
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 23 20:54:44 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: end _init.
Nov 23 20:54:44 NSA-493587239 NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 23 20:54:44 NSA-493587239 NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 23 20:54:45 NSA-493587239 NetworkManager: <info>  Wireless now enabled by radio killswitch
Nov 23 20:54:45 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: (135916272) ... get_connections.
Nov 23 20:54:45 NSA-493587239 NetworkManager:    SCPlugin-Ifupdown: (135916272) ... get_connections (managed=false): return empty list.
Nov 23 20:54:45 NSA-493587239 NetworkManager:    Ifupdown: get unmanaged devices count: 0
Nov 23 20:54:45 NSA-493587239 anacron[1126]: Anacron 2.3 started on 2009-11-23
Nov 23 20:54:45 NSA-493587239 init: apport pre-start process (1109) terminated with status 1
Nov 23 20:54:45 NSA-493587239 init: apport post-stop process (1128) terminated with status 1
Nov 23 20:54:45 NSA-493587239 anacron[1126]: Normal exit (0 jobs run)
Nov 23 20:54:46 NSA-493587239 cron[1115]: (CRON) INFO (pidfile fd = 3)
Nov 23 20:54:46 NSA-493587239 cron[1160]: (CRON) STARTUP (fork ok)
Nov 23 20:54:46 NSA-493587239 cron[1160]: (CRON) INFO (Running @reboot jobs)
Nov 23 20:54:47 NSA-493587239 gdm-binary[989]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 23 20:54:47 NSA-493587239 gdm-binary[989]: WARNING: Unable to find users: no seat-id found
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): now managed
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): bringing up device.
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): preparing device.
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Nov 23 20:54:47 NSA-493587239 kernel: [   16.881676] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Nov 23 20:54:47 NSA-493587239 kernel: [   16.938609] eth0: link down
Nov 23 20:54:47 NSA-493587239 NetworkManager: supplicant_interface_acquire: assertion `mgr_state == NM_SUPPLICANT_MANAGER_STATE_IDLE' failed
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (eth0): carrier is OFF
Nov 23 20:54:47 NSA-493587239 kernel: [   16.938853] ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (eth0): new Ethernet device (driver: 'via-rhine')
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (eth0): now managed
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (eth0): bringing up device.
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (eth0): preparing device.
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Nov 23 20:54:47 NSA-493587239 NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:12.0/net/eth0
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  modem-manager is now available
Nov 23 20:54:47 NSA-493587239 NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  Trying to start the supplicant...
Nov 23 20:54:47 NSA-493587239 gdm-simple-slave[1185]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle
Nov 23 20:54:47 NSA-493587239 NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0)
Nov 23 20:54:48 NSA-493587239 kernel: [   17.678556] __ratelimit: 6 callbacks suppressed
Nov 23 20:54:48 NSA-493587239 kernel: [   17.678560] type=1503 audit(1259027688.242:25): operation="open" pid=1227 parent=1226 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Nov 23 20:54:48 NSA-493587239 acpid: client connected from 1347[107:114]
Nov 23 20:54:48 NSA-493587239 mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Nov 23 20:54:48 NSA-493587239 kernel: [   18.055816] type=1503 audit(1259027688.618:26): operation="open" pid=1351 parent=1238 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Nov 23 20:54:49 NSA-493587239 mysqld: 091123 20:54:49 [Note] Plugin 'FEDERATED' is disabled.
Nov 23 20:54:49 NSA-493587239 kernel: [   18.804064] type=1503 audit(1259027689.370:27): operation="open" pid=1358 parent=1357 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Nov 23 20:54:49 NSA-493587239 acpid: client connected from 1200[0:0]
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50  InnoDB: Started; log sequence number 0 44233
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50 [ERROR] /usr/sbin/mysqld: Table './mysql/user' is marked as crashed and should be repaired
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50 [Warning] Checking table:   './mysql/user'
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50 [ERROR] 1 client is using or hasn't closed the table properly
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50 [ERROR] /usr/sbin/mysqld: Table './mysql/db' is marked as crashed and should be repaired
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50 [Warning] Checking table:   './mysql/db'
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50 [ERROR] 1 client is using or hasn't closed the table properly
Nov 23 20:54:50 NSA-493587239 kernel: [   20.004428] [drm] Initialized drm 1.1.0 20060810
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50 [Note] Event Scheduler: Loaded 0 events
Nov 23 20:54:50 NSA-493587239 mysqld: 091123 20:54:50 [Note] /usr/sbin/mysqld: ready for connections.
Nov 23 20:54:50 NSA-493587239 mysqld: Version: '5.1.37-1ubuntu5'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Nov 23 20:54:50 NSA-493587239 kernel: [   20.206768] type=1503 audit(1259027690.770:28): operation="open" pid=1380 parent=1379 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Nov 23 20:54:50 NSA-493587239 kernel: [   20.271917] type=1503 audit(1259027690.834:29): operation="open" pid=1391 parent=1390 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Nov 23 20:54:50 NSA-493587239 /etc/mysql/debian-start[1403]: Upgrading MySQL tables if necessary.
Nov 23 20:54:51 NSA-493587239 /etc/mysql/debian-start[1408]: Looking for 'mysql' as: /usr/bin/mysql
Nov 23 20:54:51 NSA-493587239 /etc/mysql/debian-start[1408]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Nov 23 20:54:51 NSA-493587239 /etc/mysql/debian-start[1408]: This installation of MySQL is already upgraded to 5.1.37, use --force if you still need to run mysql_upgrade
Nov 23 20:54:51 NSA-493587239 /etc/mysql/debian-start[1452]: Checking for insecure root accounts.
Nov 23 20:54:51 NSA-493587239 kernel: [   21.153418] ppdev: user-space parallel port driver
Nov 23 20:54:51 NSA-493587239 /etc/mysql/debian-start[1459]: Triggering myisam-recover for all MyISAM tables
Nov 23 20:54:52 NSA-493587239 wpa_supplicant[1191]: CTRL-EVENT-SCAN-RESULTS 
Nov 23 20:54:52 NSA-493587239 wpa_supplicant[1191]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.0/usb2
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: Failed to get parent
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.0/usb2/2-0:1.0
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:10.0/usb2
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: Device vendor/product is 1D6B:0001
Nov 23 20:54:53 NSA-493587239 mysqld: 091123 20:54:53 [ERROR] /usr/sbin/mysqld: Table './fusion/fusion_admin' is marked as crashed and should be repaired
Nov 23 20:54:53 NSA-493587239 mysqld: 091123 20:54:53 [Warning] Checking table:   './fusion/fusion_admin'
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.1/usb3
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.1/usb3/3-0:1.0
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.1/usb3/3-1
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.1/usb3/3-1/3-1:1.0
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.2/usb4
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.2/usb4/4-0:1.0
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.3/usb5
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.3/usb5/5-0:1.0
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.4/usb1
Nov 23 20:54:53 NSA-493587239 udev-configure-printer: add /devices/pci0000:00/0000:00:10.4/usb1/1-0:1.0

---

### Post by thomi_ch on 2010-03-17
Hello

I have asimilar problem with my ASUS EEEPC T91MT:
00:1b.0 Audio device: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller (rev 07)
        Subsystem: ASUSTeK Computer Inc. Device 8398
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
        Latency: 0, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 23
        Region 0: Memory at f3f38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
                Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0+,D1-,D2-,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-
        Capabilities: [70] Express (v1) Root Complex Integrated Endpoint, MSI 00
                DevCap: MaxPayload 128 bytes, PhantFunc 0, Latency L0s <64ns, L1 <1us
                        ExtTag- RBE- FLReset-
                DevCtl: Report errors: Correctable- Non-Fatal- Fatal- Unsupported-
                        RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop-
                        MaxPayload 128 bytes, MaxReadReq 128 bytes
                DevSta: CorrErr- UncorrErr- FatalErr- UnsuppReq- AuxPwr- TransPend+
                LnkCap: Port #0, Speed unknown, Width x0, ASPM unknown, Latency L0 <64ns, L1 <1us
                        ClockPM- Suprise- LLActRep- BwNot-
                LnkCtl: ASPM L0s Enabled; Disabled- Retrain- CommClk-
                        ExtSynch- ClockPM- AutWidDis- BWInt- AutBWInt-
                LnkSta: Speed unknown, Width x0, TrErr- Train- SlotClk- DLActive- BWMgmt- ABWMgmt-
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


hda-intel: spurious response 0x0:0x0, last cmd=0x270600

After a clear boot, no sound problems. After suspeding to RAM/DISK no sound, and above log entry's.

Thanks for help
thomi

---

### Post by Sin@Sin-Sacrifice on 2010-03-24
I've had about 4 or 5 lock-ups in the last 3 days and the hda-intel messages are always the last output in kern.log and dmesg. Can't find anything specifically helpful on the interwebs.

---

### Post by mfoerster on 2010-03-25
I have the same messages.  I do not lose sound but when soundcard is used the messages are none stop.

Asus m3n78-vm MB karmic 64bit :icon_frown:

---

### Post by james_fried on 2010-07-29
@Sin

Have you been able to resolve this issue?

It's been effecting my machine too. Have posted to [launchpad here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/611334"). The machine crashes HARD and randomly - about every day or so with this:

```
hda-intel: spurious response 0x0:0x0, last cmd=0x5f0700
```

J

---

### Post by m0dcm on 2010-07-30
Have any of you tried updating to the new ALSA?
I run the Acer Aspire One AO751h running Ubuntu 9.10, and had lock ups now and again, but not had any since upgrading ALSA and my GMA500 driver (Thanks to Lucazade and the Crew!!), it may be a coincidence, but worth a try?

---

### Post by james_fried on 2010-07-31
> **m0dcm said:**
> Have any of you tried updating to the new ALSA?
cheers for the suggestion m0dcm - will give that a go on monday!

---

