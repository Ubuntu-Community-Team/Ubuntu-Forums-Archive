---
title: "Wireless disconnect and reconnect?"
date: 2011-10-17
forum: General Help
---

### Post by hardisty on 2011-10-17
I have a weird issue with WiFi dropping the signal roughly every 5 or so minutes and then automatically reconnecting. Sometimes this is instant, but if I'm far enough away from the router, it could take some time. (I also question if I'm receiving the reception that I should be. It's a brand new laptop but it will get poor signal in the basement while my parent's older laptops get mid-to-high signal.)

If it helps, I had to re-set up my wireless upon install [http://ubuntuforums.org/showthread.php?t=1846928](http://ubuntuforums.org/showthread.php?t=1846928)

If anybody has any ideas, I'd love to hear them! Thanks!

---

### Post by WarrenSullivan on 2011-10-17
Do you have any of these problems with your parents laptop? did you ever run windows on the laptop, was it ok then? Most of the time signal differences of laptops are due to the quality of the wifi receiver in the laptop itself, interference is a big issue with wireless, wireless phone on the same band can kill your connection etc......

hth

---

### Post by hardisty on 2011-10-17
> **WarrenSullivan said:**
> Do you have any of these problems with your parents laptop? did you ever run windows on the laptop, was it ok then? Most of the time signal differences of laptops are due to the quality of the wifi receiver in the laptop itself, interference is a big issue with wireless, wireless phone on the same band can kill your connection etc......

hth

No problem with their laptops. I've only run Ubuntu on my own. The disconnect/reconnect problem happens on whatever wireless network I'm on, not just my home network.

---

### Post by WarrenSullivan on 2011-10-17
I personally would be trying a 3rd party wireless dongle to isolate the onboard one, another option, download a wifi signal strength meter off the net, there are a tonne out there, run it, open the ubuntu version of command prompt, execute a constant ping to your wireless router/access point, watch the signal strength and watch the ping, look for what happens when it drops....

Also, are you using DHCP? what happens if you manually assign an IP to the laptop....im thinking that the IP is being released too early....is it exactly 5 mins? time it.....

---

### Post by hardisty on 2011-11-01
This happens on my campus, too, but that's not the best wifi to begin with

---

### Post by temporos on 2011-11-03
This is happening to me, too.  I'm running Lucid (10.04.1) on an ACER netbook, and I lose my network connection once every 60 seconds or-so.  It usually reconnects again after about 60 more seconds.  This cycle is repeated endlessly.  Here's some info that might help...
```
user@host:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:"Misty Network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:25:BC:89:2A:33   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=35/70  Signal level=-75 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by temporos on 2011-11-06
Just an update...

The disconnects are becoming more frequent (about once every minute of network activity).  Now it won't automatically reconnect, though.  I have to manually disconnect (it thinks it's still connected) and reconnect.  I have this issue only on my netbook (running the UNE interface).  My notebook uses the same software, 10.04.1, but it is not having this issue.

Anyone have any ideas about what's going on?

---

