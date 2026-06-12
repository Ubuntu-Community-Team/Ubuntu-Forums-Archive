---
title: "kismet problem!"
date: 2011-04-18
forum: General Help
---

### Post by vivek.pandey on 2011-04-18
hey everyone
    i have installed kismet in my laptop and when i try to start it using the command kismet i get the following output
```

vivek@NEO:~$ sudo kismet
[sudo] password for vivek: 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Broadcom): Enabling monitor mode for bcm43xx source interface wlan0 channel 6...
FATAL: SetIFFlags: Unknown interface wlan0: Operation not possible due to RF-kill
Done.
vivek@NEO:~$ 

```
here is the output of iwconfig
```

vivek@NEO:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Monitor  Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

ppp0      no wireless extensions.

vivek@NEO:~$ 

```
anybody has a possible solution for this problem?
note:: i have broadcom driver installed...

---

