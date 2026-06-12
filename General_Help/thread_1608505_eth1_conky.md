---
title: "eth1 conky"
date: 2010-10-29
forum: General Help
---

### Post by Hippytaff on 2010-10-29
for some reason my wireless shows up as eth0

```

eth1      IEEE 802.11bg  ESSID:"TALKTALK-3E3CFB"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 1C:BD:B9:3E:3C:FB   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=-56 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

my conky
```

snip
${color #5b6dad}eth1 Down: $color${downspeed eth1}${alignr} k/s
${color #5b6dad} ${downspeedgraph eth0 16,140 000000 7f8ed3 150}
${color #5b6dad}eth1 Up:   $color${upspeed eth1}${alignr} k/s
${color #5b6dad} ${upspeedgraph eth1 16,140 000000 7f8ed3 18}

```

What am I doing wrong?

---

### Post by Brandon Williams on 2010-10-29
I'm not completely certain what you're asking. Your wireless is showing up in the system as eth1. Most of your conky config refers to eth1, with the exception of the downspeedgraph setting, which refers to eth0. Are you saying that the 3 conky config settings that refer to eth1 are not displaying the values for your wireless and that the one that refers to eth0 _is_ display the value for your wireless?

---

### Post by Hippytaff on 2010-10-29
conky displays no up or down stats. The 3 correct settings don't display anything and the one that is incorrectly set also displays nothing - I missed the fact that downspeed is set to eth0 though :-s

edit > after re-reading it appears I failed to include the fact that conky doesn't display the required info :-)
oops - I'll blame lack of sleep and a demanding wife :-) (but should just blame myself)

---

### Post by DirtyPC on 2010-10-29
> **Hippytaff said:**
> conky displays no up or down stats. The 3 correct settings don't display anything and the one that is incorrectly set also displays nothing - I missed the fact that downspeed is set to eth0 though :-s
But is your wireless working though?

---

### Post by Hippytaff on 2010-10-29
harrylucas1 - my wireless works
Brandon - thanks for pointing that out, it is displaying correctly after I edited the config file to look in the right place.

I am a true numpty - thanks both :-)

---

