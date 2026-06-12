---
title: "wpa_supplicant"
date: 2012-06-19
forum: General Help
---

### Post by santhoshkumarkv on 2012-06-19
Hi All

I am trying to connect a wifi network using wpa_supplicant
I want to connect the device using commands, how I can do it?
Please help me, 
wpa_supplicant -i wlan0 -B -c /etc/wpa_supplicant.conf

I'm working on Ubuntu Linux 12.04 LTS ver.
getting some error 
"Assosciation request to the driver failed"
and
 " WPA: 4 -way Handshake failed-pre shared key may be incorrect"

Thanks in Advance
santhosh:(

---

### Post by O2Blevel on 2012-06-19
Well, it seems I'm not the only one who doesn't like network-manager. LOL!

Here are the commands I use, make the appropriate changes.

wpa_passphrase "linksys" "12345678" > wpaconfig
sudo wpa_supplicant -iwlan0 -cwpaconfig
  (wait for the authentication process to finish)
crtl-z
bg
sudo dhclient wlan0

---

### Post by ratheeshkmrp on 2012-06-20
Hi..
I've tested as per your instructions, bt it's not working properly.
I'm getting same error message


Regards
Rp

---

### Post by O2Blevel on 2012-06-20
Sorry, but I haven't used it in a while. You need to create a file named wpaconfig.

```
network={
	ssid="your_ssid"
	#psk="your_wpa_key"
	psk=(use this http://www.wireshark.org/tools/wpa-psk.html)
}
```

If you're interested, I found that wicd makes a good replacement for network-manager.

---

### Post by ratheeshkmrp on 2012-06-21
Hii All..
could you please give detail idea about wpa_supplicant and wicd packages.
I want to connect the WiFi device using commands, how I can do it?
Please Advice me,

Regards
Rp

---

