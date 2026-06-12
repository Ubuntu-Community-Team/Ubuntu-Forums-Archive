---
title: "wep wireless no connection"
date: 2010-08-20
forum: General Help
---

### Post by jm2 on 2010-08-20
Perhaps someone can help. 

I have an hp G60-445dx notebook pc laptop. Ubuntu 9.10

the wireless was working just beautifully, with an ESSID hidden just fine.

I changed the router to use WEP security.. and for the life of me I can't get it to work.

I have tried network manager, and wicd, and iwconfig commands manually, and setting wlan0 in /etc/network/intefaces. (none of the above approaches have worked)

wicd is sort of the most promising. It wants to connect but can't get the IP address. I tried static ip, and putting in my Internet provider but still no luck.

I know the wireless router is up, as other computers in house are using wireless.

It could be that my wireless button is broken and won't go on?? but it was working.

My lspci - arthros ar5001
my ifconfig shows wlan0
my iwconfig shows wlan0 

Would I be better off getting the usb d-link wireless?

Can someone point me in the right direction?

thanks

---

### Post by davrosuk on 2010-08-20
This doesn't solve your issue but... I'd highly recommend against using WEP. The "security" it provides is roughly equivalent to leaving the keys in your door. Its also worth mentioning that hiding the SSID doesn't really hide the network either - the only person that really suffers hiding SSID's and using WEP is you. An attacker can still find your wifi and be fully attached and authenticated in literally 5 minutes. My advice: Use either WPA or WPA2 to secure the network - and make your life easier by not hiding the SSID. Its proper security and makes managing your wifi network much simpler.

---

### Post by pbrane on 2010-08-20
If you changed the Wifi security *after* you connected to your hidden network you may have to delete the connection and try connecting to it again using the "connect to hidden wireless network..." option in the networkmanager panel applet.

Also you should consider what davrosuk is saying. WEP is a relatively easy encryption to crack. WPA2 Personal would be a better choice.

---

### Post by jm2 on 2010-08-21
I have rebooted, I have added other entries. I have not been able to "delete" old entries.

I understand WPA/WPA2 is better. I will change it to use that eventually.

However at the moment, I want to be able to connect using WEP, just because I want to understand how it connects to the internet using Linux.


And I still can't get it to connect.  I found the wicd scripts and are looking at them. I'm sure I can't be the only person who can't seem to connect wireless using linux.

I know the wireless cards works, as I booted into windows, and got it to work just fine.

Any other suggestions on what needs setting to make this work?

---

### Post by jm2 on 2010-08-22
I tried the wpa2 today and no improvement.


I installed the madwifi driver today .. madwifi-0.9.4-current.tar.gz

i removed gnome network manager, I re-installed wicd - Now wicd won't find any wireless devices. (I don't have the /var/lib/wicd/000xxx file now either.)

I've set the advanced tab .. to wext, madwifi and no improvement

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

******* I have no clue why it's showing wifi0 **and ath0 *****
My ifconfig:

wifi0     Link encap:UNSPEC  HWaddr 00-24-2C-8D-24-93-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:1656 (1.6 KB)
          Interrupt:23 

dmesg:
[   19.189177] wifi0: Atheros AR2425 chip found (MAC 14.2, PHY SChip 7.0, Radio 10.2)
[   19.205344] ath_pci: wifi0: Atheros 5424/2424: mem=0xc2000000, irq=23


 lsmod | grep ath_pci
ath_pci               197268  0 
wlan                  228848  5 wlan_wep,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               397504  3 ath_rate_sample,ath_pci


sudo ifconfig ath0 up
sudo iwconfig ath0 key off
sudo iwconfig ath0 mode Managed
sudo iwconfig ath0 essid "xxxxx"
sudo iwconfig ath0 key [1] xxxxx
sudo dhclient ath0

Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:24:2c:8d:24:93
Sending on   LPF/ath0/00:24:2c:8d:24:93
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11

Can anyone give me some other place to look for stuff to try?
I know I can't be the only one with this wireless issue.
uname -mr
2.6.31-22-generic i686

HPG60-445DX Notebook PC

The atheros card can't be all that hard. It was working with no security. Now with WEP or WPA it is like it can't connect correctly.

Thanks

---

