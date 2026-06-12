---
title: "Please help with my wifi"
date: 2006-04-01
forum: General Help
---

### Post by rhomsy on 2006-04-01
I have a U.S. Robotics wifi card (model USR5410), which the Ubuntu wiki says it just works out of the box.

Well, using the gnome network config it sees the card, and when I click on configure, it sees my wifi network (which doesn't have a password), but the internet doesn't work.

When I type iwconfig at the prompt, I get this:
rhomsy@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet8    no wireless extensions.

vmnet1    no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"Shivaland"  Nickname:"acx100 v0.2.0pre8"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:03:93:EB:BC:E7
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality=52/100  Signal level=34/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:0   Missed beacon:0

I know those RX invalid statements tell me that something is wrong, and I know this card is supported.  I read through all the wiki stuff I could find, but I don't know what to do.  Notice that it does see my ESSID correctly (shivaland).  What should I do next?  

Thanks in advance.

---

### Post by DJ Scribblinni on 2006-04-01
Dude, post your $ ifconfig
Another thing off the top of my head to mention, if you are using a WEP key, make sure it was typed in correctly...

---

