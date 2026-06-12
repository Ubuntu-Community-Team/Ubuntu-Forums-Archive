---
title: "Natty Narwhal wont let me put in my wep key"
date: 2011-05-17
forum: General Help
---

### Post by ryuguns on 2011-05-17
I'm using ubuntu 11.04, I type in my wep key correctly and when I fill it out completely it doesn't let me press the connect button.


I assume it's a restriction of the amount of characters I use?

---

### Post by IWantFroyo on 2011-05-17
Try the following for a hex WEP key:
```
sudo iwconfig wlan0 essid "Your SSID (with the "s)" key WEPKEY
```
For the ascii key:
```
sudo iwconfig wlan0 essid "Your SSID (with the "s)" S: WEPKEY
```

If I get something wrong in the ascii key area, could someone help out? Thanks.

---

