---
title: "Connect to wireless adhoc from terminal"
date: 2010-11-23
forum: General Help
---

### Post by spiky001 on 2010-11-23
Ok I want to connect to my wireless adhoc network using terminal, the networks works ok with network manager I can connect to Infastuructuers ok, both of these work ```
sudo iwconfig wlan0 essid NETWORK_ID key s:WIRELESS_KEY
``````
ifconfig wlan0 down
iwconfig wlan0 mode managed
iwconfig wlan0 key "Key"
iwconfig wlan0 channel "Channel"
iwconfig wlan0 essid "Essid"
dhclient wlan0
```They dont work with adhoc is there something i need to change

---

### Post by spiky001 on 2010-11-26
bump plz

---

### Post by iponeverything on 2010-11-26
some adapters don't do ad-hoc.

After running this:

```
sudo iwconfig wlan0 mode ad-hoc 

```

what does the iwconfig command show?

---

### Post by spiky001 on 2010-11-26
It returns unknown command, although I can connect using network manager ok just from terminal it wont

---

