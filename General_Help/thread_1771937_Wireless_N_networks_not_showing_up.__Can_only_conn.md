---
title: "Wireless N networks not showing up.  Can only connect to G networks."
date: 2011-05-30
forum: General Help
---

### Post by bearaids on 2011-05-30
I just bought a wireless N router, but can't get any of the N channels to show up on my Ubuntu 10.10 desktop.  I know the signal is strong, as my laptop can access them.  I need to get the N network working, any ideas on what is wrong?

When I run *lspci -v | less* I get:    
    
    [PHP]04:00.0 Network controller: RaLink RT2860
       Subsystem: ASUSTeK Computer Inc. Device 130f
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at fb500000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: rt2800pci
        Kernel modules: rt2860sta, rt2800pci[/PHP]

This is the link to the newest driver[http://www.asus.com/Networks/WiFi_Networking/PCEN13/#download]("http://www.asus.com/Networks/WiFi_Networking/PCEN13/#download").  Do I need to update the driver?  After I downloaded it, any guides on how to install manually?

---

### Post by linuxinstalledfromhdd on 2011-05-30
Do you have the little wireless icon in the taskbar showing?  Were you able to ever hook anything to your Ubuntu wirelessly since installed?

---

### Post by bearaids on 2011-05-30
Yes, I can see the icon and connect to my G networks.  I just can't see or connect to my N networks.  Its almost like my card is configured to just accept a/b/g connections, and not the higher speed N ones.

---

### Post by linuxinstalledfromhdd on 2011-05-30
I would cross reference your specs on google search engine with the manufacture of your wifi router and the card you are using. See if they are actually truly compatible or not.

---

### Post by 5149.5 on 2011-05-30
Check this[ link]("http://goo.gl/cudZb"). It sounds like you need to load a data file to activate on  802.11N.

---

### Post by garvinrick4 on 2011-05-30
So you bought an N router and have a N card, not a dual band correct.
So in your router in Wireless set to 20 and 40 mhz and will connect to card at 2.4 ghz
at N speeds. If you have a lot of routers around you change your channel to 1 or 11
in router as they all default to 6 so as far as you can get away is 1 or 11.
You most likely have set at 20mhz only instead of 20 or 40 mhz in 2.4 ghz range.
This is dual band so just use 2.4 ghz settings for you. Notice I have network mode set as mixed instead
of just N. Because my linux driver in intel card will only work in G (iwlagn is driver). But other Operating Systems work in N.
So I choose mixed so I get them both G and N. If you want to use both 5.0 and 2.4 signals have to have router and card that
support channel bonding. (Dual Band router and supporting card)
**Fastest speed I have gotten is 144 Mb/s at N speeds. You will get tops of 54 Mb/s at G speeds. Hope you can get to 144.

---

### Post by garvinrick4 on 2011-05-31
> **bearaids said:**
> Yes, I can see the icon and connect to my G networks.  I just can't see or connect to my N networks.  Its almost like my card is configured to just accept a/b/g connections, and not the higher speed N ones.
You can run
iwconfig
If will tell you if card is running at gbn or just bg as below:
rick@rick-HP:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Home"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: C0:C1:C0:C6:0A:EC   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:336   Missed beacon:0

---

### Post by bearaids on 2011-05-31
apparently my card is running on an N network. I diagnosed my problem. My card only supports 2.4ghz, where as the network I was trying to connect to was my 5ghz network.  There is not an issue with any settings on my computer, just a hardware limitation of my card.

thanks everyone for the help.

---

### Post by garvinrick4 on 2011-05-31
> **bearaids said:**
> apparently my card is running on an N network. I diagnosed my problem. My card only supports 2.4ghz, where as the network I was trying to connect to was my 5ghz network.  There is not an issue with any settings on my computer, just a hardware limitation of my card.

thanks everyone for the help.

If you show a lot of SSID's for other machines in area with routers if you do change the 
2.4 ghz channel to 1 or 11 will get off by yourself and not be fighting everyone for the default
channel 6. Most do not get into it and just leave router settings at default for 2.4 ghz and channel 6. 
I set mine at 1 and I am only one on block using that channel, nice. I would imagine in an apartment 
building or a dorm room could be a big fight over best signals there.
Most can type 192.168.1.1 in URL and get router, type in user name and password for router and make change.
or your Default route.

---

