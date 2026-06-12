---
title: "wpa_supplicant usage Question"
date: 2006-03-01
forum: General Help
---

### Post by crxyem on 2006-03-01
well , I've got wpa runing niceley on my home network, I followed the infro from [https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto) and all is well. 

my question is can  Iinclude multiple network info in my wpa_supplicant.conf, so that when I'm at work, I can authenticate to the AP at work., and when at home and I boot my lapop, have it authenticate to my home AP

I have edited my /etc/network/interfaces to look like this to get a dhcp address from my AP
```
  
 auto wlan0
  iface wlano inet dhcp
  pre-up /etc/init.d/wpasupplicant start
  pre-up sleep 5

```

I have edited my wpa_supplicant.conf file to include the following to connect at home.

```
network={
        ssid="myessid"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
        psk=mykey
  }
```

can I simply make my config file look like this and assume that wpa_suplicant will connect to whatever 
AP I'm near:

```
network={
        ssid="myhomeessid"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
        psk=myHomekey
  }
network={
        ssid="myworkessid"
        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
        psk=myworkkey
  }

```

or is there a different or better way to do this ??

---

### Post by ssalman on 2006-03-01
according to the below link you should be able to do just what you discribed. give it a try and post your findings. good luck.

[http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain](http://hostap.epitest.fi/cgi-bin/viewcvs.cgi/*checkout*/hostap/wpa_supplicant/wpa_supplicant.conf?rev=HEAD&content-type=text/plain)

---

