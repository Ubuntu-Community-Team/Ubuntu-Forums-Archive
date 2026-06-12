---
title: "Major Wi-Fi issues after installing Ubuntu 11.10 - please help!"
date: 2011-10-20
forum: General Help
---

### Post by Takehaniyasubiko on 2011-10-20
Hi,

I am using Ubuntu for 3 years now and it's been a rough ride, but I managed to get things done... until now. I have RTL8187 Wi-Fi card in my Amilo Li3710 and it worked like a charm before, but now **after every** 2-3 minutes I get tons of tx excessive retries and invalid miscs and it causes extremely slow downloads. It goes down from 13 MB/s to 1 MB/s. 

Here's my iwconfig output:
```
wlan0     IEEE 802.11bg  ESSID:"Neostrada"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:1A:6B:C1:39:E6   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:292  Invalid misc:17093   Missed beacon:0
```My router is next to my laptop and the link quality is excellent. I've tried all available tips on Wi-Fi issues in Ubutnu, but nothing helped. :(

Please help!

---

### Post by Takehaniyasubiko on 2011-10-20
I think the newest kernel update fixed this.

I *think* because I'm still getting some errors, but the download speed didn't go down yet. I hope it will stay this way because the Wi-Fi issues were my only issues in 11.10.

EDIT: Nope. **The problem remains.** 

:(

---

### Post by Takehaniyasubiko on 2011-10-21
It's funny how I talk with myself, but whatever.

I've changed the Wi-Fi mode from g to b+g and it helped. I still get a lot of tx excessive retries, but the invalid misc are not going over 100 even after hours and the download speed isn't going down. Before the kernel update the mode change didn't help so something must have changed for the better because of the said update.

EDIT: NO! Everything started all over again! Nothing helps in the long run!

I love Ubuntu, but the Wi-Fi support is a mess. ](*,)

---

### Post by Takehaniyasubiko on 2011-10-23
It's an issue with  Kernel 3.0. Anybody knows when this might get fixed?

---

### Post by ratcheer on 2011-10-23
I searched on "wifi retries" on Launchpad and got about ***6000 **pages*** of hits.

Tim

---

### Post by Takehaniyasubiko on 2011-10-23
Over [s]9000[/s] 6000 pages of hits, and yet it's not fixed.

It's funny since this goes way back to at least 8.04. It was fixed at one point, but now it's broken all over again.

---

