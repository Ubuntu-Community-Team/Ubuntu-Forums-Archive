---
title: "Help with Configuring wpa_supplicant.conf"
date: 2006-03-30
forum: General Help
---

### Post by Hangetsu on 2006-03-30
I'm at wit's end, so I hope you all can give me the definitive answer on how I should configure my wpa_supplicant.conf file.  Here's my environment:

WPA2 (AES) protected access point, not broadcasting my ssid of "SBHomeNet"
Using ndiswrapper to configure my wireless card
ndiswrapper and wpasupplicant installed

Here is what I have in my current wpa_supplicant.conf file (not the full file, but what I've changed):
> ap_scan = 2

network={
     ssid="SBHomeNet"
     proto=RSN
     key_mgmt=WPA-PSK
     pairwise=CCMP
     psk=<encrypted>
}

Is there anything I've misconfigured above that would cause me not to connect to my access point?  The frustrating part is I didn't save this file off when I got this to work before.

---

### Post by Hangetsu on 2006-03-30
Hold on, I might have this... On the plus side, Im getting a better understanding of wireless networking in general through all of this!

---

