---
title: "Logged Errors climb into GB range fast"
date: 2010-12-02
forum: General Help
---

### Post by held7over on 2010-12-02
I have had this happening off and on, since I moved to Ubuntu 10.04, via clean install. I did pick EXT4, which is the only difference I can think of.

What happens is, 3 of my log files suddenly start filling fast with "Unknown" errors. The three files are kern.log messages and syslog. All three files will have about the same measurement of size. It can take a few weeks or it can speed along fairly fast and use up my free space of 6 GB. For instance, today, I blanked the three files and within the space of about 4 hours they grew to almost 2 GB each!  I blanked them again and rebooted, and in 3 hours they only grew to 5 MB each.

Below is a sample which shows where the "unknown" errors start. The first such error is in **BOLD** so that it is easy to find. Once they start happening there is little else printed in the logs. Does anyone know how to track down what is happening and fix this? :D

Dec  1 22:11:05 ispy kernel: [   26.553797] Console: switching to colour frame buffer device 210x65
Dec  1 22:11:05 ispy kernel: [   26.653060] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
Dec  1 22:11:05 ispy kernel: [   26.653088] cfg80211: Calling CRDA for country: CO
Dec  1 22:11:05 ispy kernel: [   26.654314] au8830 0000:00:10.0: enabling device (0104 -> 0107)
Dec  1 22:11:05 ispy kernel: [   26.654346] au8830 0000:00:10.0: PCI INT A -> Link[LNKD] -> GSI 9 (level, low) -> IRQ 9
Dec  1 22:11:05 ispy kernel: [   26.654482] Vortex: init.... 
Dec  1 22:11:05 ispy kernel: [   26.690350] cfg80211: Regulatory domain changed to country: CO
Dec  1 22:11:05 ispy kernel: [   26.690367] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Dec  1 22:11:05 ispy kernel: [   26.690379] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Dec  1 22:11:05 ispy kernel: [   26.690389] 	(5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
Dec  1 22:11:05 ispy kernel: [   26.690400] 	(5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
Dec  1 22:11:05 ispy kernel: [   26.690410] 	(5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
Dec  1 22:11:05 ispy kernel: [   27.378480] done.
Dec  1 22:11:05 ispy kernel: [   27.511023] gameport: AU88x0 Gameport is pci0000:00:10.0/gameport0, speed 1754kHz
Dec  1 22:11:05 ispy kernel: [   31.031521] type=1505 audit(1291266665.865:5):  operation="profile_load" pid=778 name="/usr/share/gdm/guest-session/Xsession"
Dec  1 22:11:05 ispy kernel: [   31.086331] type=1505 audit(1291266665.921:6):  operation="profile_replace" pid=779 name="/sbin/dhclient3"
Dec  1 22:11:05 ispy kernel: [   31.087947] type=1505 audit(1291266665.921:7):  operation="profile_replace" pid=779 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
Dec  1 22:11:05 ispy kernel: [   31.102454] type=1505 audit(1291266665.937:8):  operation="profile_replace" pid=779 name="/usr/lib/connman/scripts/dhclient-script"
Dec  1 22:11:06 ispy kernel: [   31.197103] type=1505 audit(1291266666.033:9):  operation="profile_load" pid=780 name="/usr/bin/evince"
Dec  1 22:11:06 ispy kernel: [   31.336167] type=1505 audit(1291266666.173:10):  operation="profile_load" pid=780 name="/usr/bin/evince-previewer"
Dec  1 22:11:06 ispy kernel: [   31.406795] type=1505 audit(1291266666.241:11):  operation="profile_load" pid=780 name="/usr/bin/evince-thumbnailer"
Dec  1 22:11:06 ispy kernel: [   31.513129] type=1505 audit(1291266666.349:12):  operation="profile_load" pid=850 name="/usr/lib/cups/backend/cups-pdf"
Dec  1 22:11:06 ispy kernel: [   31.515104] type=1505 audit(1291266666.349:13):  operation="profile_load" pid=850 name="/usr/sbin/cupsd"
Dec  1 22:11:06 ispy kernel: [   31.548152] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Dec  1 22:11:06 ispy kernel: [   31.552901] type=1505 audit(1291266666.389:14):  operation="profile_load" pid=851 name="/usr/sbin/tcpdump"
Dec  1 22:11:06 ispy kernel: [   31.585318] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Dec  1 22:11:08 ispy kernel: [   33.331556] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
Dec  1 22:11:08 ispy kernel: [   33.342832] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
**Dec  1 22:11:09 ispy kernel: [   34.526314] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=224.0.0.251 LEN=164 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=144** 
Dec  1 22:11:10 ispy kernel: [   35.554517] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=224.0.0.251 LEN=221 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=201 
Dec  1 22:11:10 ispy kernel: [   35.719383] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=224.0.0.251 LEN=136 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=116 
Dec  1 22:11:10 ispy kernel: [   36.075929] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=224.0.0.251 LEN=233 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=213 
Dec  1 22:11:11 ispy kernel: [   36.546402] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=8.8.4.4 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=62021 PROTO=UDP SPT=45720 DPT=53 LEN=31 
Dec  1 22:11:11 ispy kernel: [   36.715473] Unknown InputIN=eth0 OUT= MAC=00:40:f4:72:89:f1:00:1a:70:fd:ab:01:08:00 SRC=8.8.4.4 DST=192.168.2.200 LEN=126 TOS=0x00 PREC=0x00 TTL=53 ID=19997 PROTO=UDP SPT=53 DPT=45720 LEN=106 
Dec  1 22:11:11 ispy kernel: [   36.716500] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=8.8.4.4 LEN=51 TOS=0x00 PREC=0x00 TTL=64 ID=62022 PROTO=UDP SPT=33873 DPT=53 LEN=31 
Dec  1 22:11:11 ispy kernel: [   36.909763] Unknown InputIN=eth0 OUT= MAC=00:40:f4:72:89:f1:00:1a:70:fd:ab:01:08:00 SRC=8.8.4.4 DST=192.168.2.200 LEN=126 TOS=0x00 PREC=0x00 TTL=53 ID=32088 PROTO=UDP SPT=53 DPT=33873 LEN=106 
Dec  1 22:11:11 ispy kernel: [   37.039360] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=8.8.4.4 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=65331 DF PROTO=UDP SPT=33316 DPT=53 LEN=40 
Dec  1 22:11:11 ispy kernel: [   37.098220] Unknown InputIN=eth0 OUT= MAC=00:40:f4:72:89:f1:00:1a:70:fd:ab:01:08:00 SRC=8.8.4.4 DST=192.168.2.200 LEN=121 TOS=0x00 PREC=0x00 TTL=53 ID=19998 PROTO=UDP SPT=53 DPT=33316 LEN=101 
Dec  1 22:11:11 ispy kernel: [   37.098628] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=8.8.4.4 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=65346 DF PROTO=UDP SPT=36616 DPT=53 LEN=40 
Dec  1 22:11:12 ispy kernel: [   37.160579] Unknown InputIN=eth0 OUT= MAC=00:40:f4:72:89:f1:00:1a:70:fd:ab:01:08:00 SRC=8.8.4.4 DST=192.168.2.200 LEN=121 TOS=0x00 PREC=0x00 TTL=53 ID=42765 PROTO=UDP SPT=53 DPT=36616 LEN=101 
Dec  1 22:11:12 ispy kernel: [   37.160942] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=8.8.4.4 LEN=60 TOS=0x00 PREC=0x00 TTL=64 ID=65362 DF PROTO=UDP SPT=50233 DPT=53 LEN=40 
Dec  1 22:11:12 ispy kernel: [   37.219689] Unknown InputIN=eth0 OUT= MAC=00:40:f4:72:89:f1:00:1a:70:fd:ab:01:08:00 SRC=8.8.4.4 DST=192.168.2.200 LEN=76 TOS=0x00 PREC=0x00 TTL=53 ID=42766 PROTO=UDP SPT=53 DPT=50233 LEN=56 
Dec  1 22:11:12 ispy kernel: [   37.321123] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=91.189.94.4 LEN=76 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56 
Dec  1 22:11:12 ispy kernel: [   37.529974] Unknown InputIN=eth0 OUT= MAC=00:40:f4:72:89:f1:00:1a:70:fd:ab:01:08:00 SRC=91.189.94.4 DST=192.168.2.200 LEN=76 TOS=0x00 PREC=0x00 TTL=38 ID=0 DF PROTO=UDP SPT=123 DPT=123 LEN=56

---

### Post by plucky on 2010-12-02
Do you use wired or wireless lan connection?

> Dec 1 22:11:09 ispy kernel: [ 34.526314] Unknown OutputIN= OUT=eth0 SRC=192.168.2.200 DST=224.0.0.251 LEN=164 TOS=0x00 PREC=0x00 TTL=255 ID=0 DF PROTO=UDP SPT=5353 DPT=5353 LEN=144 

Something is trying to use your wired connection.

---

### Post by held7over on 2010-12-02
Hi plucky! This is a desktop system with both wired and wireless capabilities. However, I only use the _hard wired_ connection to my Linksys router. 

I have set this desktop computer to have a static IP address of 192.168.2.200 on my home network.

When you say 'something is trying to use my wired connection' is it coming from outside my network or is it some program internal to my computer??? And how do we track it down?

---

### Post by Decatf on 2010-12-02
Those are firewall logs. Disable or reduce your firewall log verbosity level.

I can see that there's even your DNS requests. It seems to be spewing everything unecessarily.

---

### Post by held7over on 2010-12-02
I don't know anything about firewalls at all, and so googled 'Ubuntu Firestarter Verbosity' and discovered Firestarter, which is what I use, doesn't provide a good way to turn verbosity off. 

I settled upon a solution of #-ing out the following 3 lines at the end of file /etc/firestarter/firewall:

# --------( Unsupported Traffic Catch-All )--------

$IPT -A INPUT -j LOG_FILTER
#$IPT -A INPUT -j LOG --log-level=$LOG_LEVEL --log-prefix "Unknown Input"
$IPT -A OUTPUT -j LOG_FILTER
#$IPT -A OUTPUT -j LOG --log-level=$LOG_LEVEL --log-prefix "Unknown Output"
$IPT -A FORWARD -j LOG_FILTER
#$IPT -A FORWARD -j LOG --log-level=$LOG_LEVEL --log-prefix "Unknown Forward"

I am going to blank the affected log files, reboot my machine, and then see if the problem is gone.

Maybe I need to explore learning a new firewall?

---

