---
title: "wireless problem...another one"
date: 2006-04-04
forum: General Help
---

### Post by smokey_ketchup on 2006-04-04
Hi 

<insert newbie disclaimer here>

I have a strange problem regarding my wireless connection. Firstly I cannot connect at boot, but that issue is for anouther thread. My actual problem is that after boot if I reload my network driver (clears all network options):

```
modprobe -r ipw2100
modprobe ipw2100
```

and then if I enter the following commands I can connect:
```
iwconfig wlan0 essid <my_essid>
iwconfig wlan0 key <my_key>
dhclient wlan0
```


but if I try I the following method, I cannot connect :confused: 
```
ifup wlan0 
```

my /etc/network/interfaces file includes the following lines

```
iface wlan0 inet dhcp
  wireless-essid <my_essid>
  wireless-key <my_key>
```


Giving the settings in my interface file I thought the two methods would be equivalent, but that does not appear to be the case?

Sorry I forgot to mention my machine (r40 thinkpad) is running kubuntu 5.10.


Hope somebody could clear this one up for me

---

### Post by steffennielsen on 2006-04-06
Do you use spaces in your essid? (or any odd characters?)

...Most people are better off with bssid-addresses! (MAC-addresses)

wireless-bssid FFFFFFFFFFFF
wireless-key XXX

...I hope it works!

---

