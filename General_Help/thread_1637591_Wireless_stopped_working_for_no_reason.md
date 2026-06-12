---
title: "Wireless stopped working for no reason"
date: 2010-12-04
forum: General Help
---

### Post by TheDesertDragon on 2010-12-04
So I was merrily downloading ArchLinux to try it in VirtualBox, and a little over halfway there the wireless just shuts off. DOwnload speed goes down to 0 and here I am.

When I connect to the network, which uses WPA2 Personal, nothing simply happens. It just looks for the network for a minute then finally gives up and prompts me for the password again.

The network is fine though - because Windows 7 on the same computer connects. 

iwconfig wlan0 output:
```

wlan0    IEEE 802.11abg  ESSID:off/any
         Mode:Managed  Frequency:2.472 GHz  Access Point: Not-Associated
         Tx-Power=15dBm
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management: off
```

Which it shouldn't be doing because I'm trying to connect to a network called 507.

I tried running the command for the first 5 seconds or so after attempting to connect, and I got this instead:

```

wlan0    IEEE 802.11abg  ESSID:"507
         Mode:Managed  Frequency:2.472 GHz  Access Point: 00:17:3F:5D:7C:7D
         Bit-rate=5.5Mb/s   Tx-Power=15 dBm
         Retry  long limit:7   RTS thr:off   Fragment thr:off
         Power Management: off
         Link Quality=70/70  Sginal level=-29 dBm
         Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
         Tx excessive retries:0  Invalid misc:0  Missed beacon:0
```

That looks much more right but it doesn't really happen though so...

I tried rebooting. It doesn't help.

Halp! =(

EDIT:
And I just hit the laptop semi-hard near the network-card and now it works.
Now the only mystery left to solve is why it worked on Windows... >.<

I've had this PC sent in for repairs a once for having a momentarily failing network card. Well, now it's failing again it seems. Been half a year.

Now the only mystery left to solve is why it worked in Windows.

---

