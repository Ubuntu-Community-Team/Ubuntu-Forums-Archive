---
title: "WPA wireless crashes (9.10)"
date: 2010-02-26
forum: General Help
---

### Post by majest on 2010-02-26
I just updated my desktop computer to a WPA enabled wireless network card.

I used to connect easily to it from Ubuntu laptop (EEEPC 1000) using WEP, but not with the new card. I left click on the wireless icon and it shows the SSID but when I try to connect the wireless icon just disappears. It looks like the network manager crashes out, no message or anything.

FYI I also have a windows xp laptop (also EEEPC 1000) which happily connects to the new network so I know it is set up correctly.

Any suggestions how to diagnose this problem??

---

### Post by yavoh on 2010-02-26
Try installing and using the WICD network manager instead of the default Ubuntu one (and remove the Ubuntu one- its name escapes me right now).  That solved a lot of WPA-related problems for me.

---

### Post by majest on 2010-02-27
> **yavoh said:**
> Try installing and using the WICD network manager instead of the default Ubuntu one (and remove the Ubuntu one- its name escapes me right now).  That solved a lot of WPA-related problems for me.

OK - i just did that. It's a lot more intuitive and no longer crashes. However it  doesn't connect :(

I can connect to my neighbor's unsecured network tho :)

From a little research on google, I tried to configure the WPA protocol using a template. The card calls it WPA-NONE with AES... this is largely gibberish to me, but anyway I made a template as follows:

/etc/wicd/encryption/templates$ more wpa-none

name = WPA-NONE
author = xxx
version = 1
require key *Key
-----
ctrl_interface=/var/run/wpa_supplicant
network={
    mode=1
    ssid="$_ESSID"
    key_mgmt=WPA-NONE
    group=CCMP
    psk="$_PSK"
}


It shows up in wicd in the menu but does not connect to my network.

---

