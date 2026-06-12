---
title: "wireless card working in Mepis but not Ubuntu"
date: 2006-03-25
forum: General Help
---

### Post by flammenwurfer on 2006-03-25
Ok, I have a Hawking HWP54G pci  card.  It's working great in Mepis, but I can't get it to a connect to my AP in Ubuntu.  I have the windows driver installed using ndisgtk and I've entered the Essid and wep key in the Network window and activated wlan0.  However I'm still not able to ping anything.  I also get nothing when I do "iwlist wlan0 scan"  in Ubuntu

Here is my iwconfig from Ubuntu Breezy

wconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"KempoTiger"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.


Here is my iwconfig in Mepis 

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"KempoTiger"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:17:48:FD:02
          Bit Rate:48 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Power Management:off
          Link Quality:100/100  Signal level:-67 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

---

### Post by flammenwurfer on 2006-03-25
anyone?  I think I've almost got it working, but I don't know what's keeping it from connecting.  Thanks

---

### Post by harisund on 2006-03-25
[http://ubuntuforums.org/showpost.php?p=861833&postcount=13](http://ubuntuforums.org/showpost.php?p=861833&postcount=13)

---

