---
title: "yet another Acer wireless problem..."
date: 2006-03-03
forum: General Help
---

### Post by clearscreen on 2006-03-03
My Acer 5023WMLI laptop just doesnt properly installs my Wireless network card.. I have tried acer-hk + ndiswrapper with the bcmwl5.inf drivers(also the bcmwl5a.inf driver), which is supposed to install it on wlan0.. however, ubuntu detected it on install as eth0 but even though I power it up in the networking screen, it does not connect to my AP, there's no sign of the wlan0 adapter that supposedly had to be installed by ndiswrapper...

ndiswrapper -l gives:
bcmwl5    driver present,hardware present

iwconfig shows the adapter but says that tx-power and all that stuff are OFF. when I try iwconfig eth0(because there's no sign of wlan0) txpower on, it says:
Set failed on device eth0 ; No such device...

I followed all the instructions on the big acer wireless topics and read all the pages, unfortuneatly no solution..

I also tried the following, this is what the ndiswrapper sourceforge pages told me:
# Driver: ndiswrapper v1.3rc1 with bcmwl5a.inf or bcmwl5.inf (either works) [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/) (Broadcom, 12/22/2004, v3.100.46.0)
# Other: acerhk v0.5.27 compiled and loaded with /sbin/modprobe acerhk autowlan=1 poll=0 force_series=5020 verbose=3 usedritek=1. wlan0 can be activated with ifup or the Network Configuration GUI tool. The LED button blinks very dimly when the card is searching for APs. 

Nothing again... :(
I've also read something about acer_acpi but Im not sure what it is and whether it will fix my wireless..

Can anyone please help me out? Thanks in advance \\:D/

---

### Post by clearscreen on 2006-03-03
Ok now I did a /etc/init.d/networking restart.. and this error came up:

firmware_helper[3819]: main: error loading '/lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/0000:06:05.0' with driver 'bcm43xx driver 0.0.1'
[4294957.881000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

Then it does DHCPDISCOVER commands but then it does send_packet: Network is down..

help :/

---

### Post by mooswa on 2006-03-07
You may want to try linuxant driverloader instead of ndiswrapper. They have 30 day free trial.

---

