---
title: "Wifi extremely slow (tried most solutions)"
date: 2012-05-20
forum: General Help
---

### Post by hvo2k on 2012-05-20
I've been using Ubuntu 11.10 for a while and suddenly today my wifi was extremely slow (still a beginner). I've tried most solutions to fixing this via

 - turning off power management 
 -echo &#8220;#disable ipv6&#8243; | sudo tee -a /etc/sysctl.conf
echo &#8220;net.ipv6.conf.all.disable_ipv6 = 1&#8243; | sudo tee -a /etc/sysctl.conf
echo &#8220;net.ipv6.conf.default.disable_ipv6 = 1&#8243; | sudo tee -a /etc/sysctl.conf
echo &#8220;net.ipv6.conf.lo.disable_ipv6 = 1&#8243; | sudo tee -a /etc/sysctl.conf
  -sudo -s
gksu gedit /etc/modprobe.d/ath9k.conf
at the end of the file add this:

options ath9k nohwcrypt=1

Those are some of the things I've tried nothing seems to work. My computer is a compaq presario CQ60.

This is what i get when i do iwconfig-

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Dynex"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1C:DF:EF:CC:81   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:75  Invalid misc:191   Missed beacon:0

Im opened to any solutions or advice on how to get my wifi back to top speed.

---

### Post by hvo2k on 2012-05-20
Some of the 0's and : are turning into face icons sorry

---

### Post by kingocounty on 2012-05-21
Hi hvo2k, like yourself, I tried everything to get my wireless back up to speed with the ath9k driver (I'm assuming that's the driver you currently have in use) under Ubuntu 11.10 (and now 12.04).  None of the recommended fixes worked for me, such as disabling wireless N or hardware encryption.

In the end, I ended up using an old Win XP driver from the Atheros website and Ndiswrapper and now I'm cooking along at top speed!

I'm using 12.04 and I had to install Ndiswrapper from the terminal using this:

sudo apt-get install ndiswrapper-dkms

You can find the Atheros drivers here:

[http://www.atheros.cz/atheros-wireless-download.php?chipset=38&system=2](http://www.atheros.cz/atheros-wireless-download.php?chipset=38&system=2)

Make sure you choose the appropriate 32 or 64 bit inf. file when installing.  Instructions for using Ndiswrapper can be found here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Just be sure to remove and blacklist the ath9k driver before you install the new one.  I hope that helps!

---

