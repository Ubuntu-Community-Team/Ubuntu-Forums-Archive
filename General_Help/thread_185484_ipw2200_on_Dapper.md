---
title: "ipw2200 on Dapper"
date: 2006-05-31
forum: General Help
---

### Post by mback on 2006-05-31
I am not able to get WPA working on my ipw2200 in my T43 Thinkpad ](*,).  Now the card worked out of the box with dapper & I am able to log into open networks -- I just can not get WPA working.

I have carefully followed the guide on how to pull in the firmware and latest versions of ieee, ipw drivers, and wpa_supplicant (following the guide for the previous versions of Umbuntu) but was unsuccessful.

Is there anything additional I need to do to get WPA working?  Is there a different location that I should put firmware, or some other suggestion that someone can help me with?

---

### Post by antealin on 2006-06-03
Have you read the documentation for your new version of wpa_supplicant?
I just upgraded to Dapper, and I noticed that wpa_supplicant didn't work.
I reinstalled it, and noticed that there were some changes in the configuration.

Go to /usr/share/doc/wpasupplicant/ and zcat README.Debian.gz NEWS.Debian.gz, and read README.modes... Also, take a look in the examples directory...
I dont have time to explain how to do it, but I guess you'll be fine by reading the examples :)

Good luck :)

---

### Post by tritonph on 2006-06-03
Do you use encryption?  

I tried this when setting my key and it worked.

iwconfig eth0 key 1 <your key>

1 is the first wep key.                       


[QUOTE=mback]I am not able to get WPA working on my ipw2200 in my T43 Thinkpad ](*,).  Now the card worked out of the box with dapper & I am able to log into open networks -- I just can not get WPA working.

I have carefully followed the guide on how to pull in the firmware and latest versions of ieee, ipw drivers, and wpa_supplicant (following the guide for the previous versions of Umbuntu) but was unsuccessful.

Is there anything additional I need to do to get WPA working?  Is there a different location that I should put firmware, or some other suggestion that someone can help me with?[/QUOTE]

---

### Post by rayanez on 2006-06-05
I made wpa work on my ipw2200 wireless card by using the generic driver "wext" instead of "ipw".

Here is the /etc/network/interfaces

---
auto eth1
iface eth1 inet dhcp
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf.local
---

and /etc/wpa_supplicant/wpa_supplicant.conf.local

---
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="mywifi"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=mypassphrasegeneratedwithwpa_passphrare
}
---

Ricardo Yanez

---

### Post by speckone on 2006-06-15
This worked great for me.  Thanks.  I think it would be great if this could make it into the [WPAHowTo]("https://wiki.ubuntu.com/WifiDocs/WPAHowTo?action=show&redirect=WPAHowto").

---

### Post by nelsonb73 on 2006-06-20
[QUOTE=rayanez]I made wpa work on my ipw2200 wireless card by using the generic driver "wext" instead of "ipw".

Here is the /etc/network/interfaces

---
auto eth1
iface eth1 inet dhcp
        wpa-driver wext
        wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf.local
---

and /etc/wpa_supplicant/wpa_supplicant.conf.local

---
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="mywifi"
        scan_ssid=1
        proto=WPA
        key_mgmt=WPA-PSK
        psk=mypassphrasegeneratedwithwpa_passphrare
}
---

Ricardo Yanez[/QUOTE]


Can I ask where you found the options for the wpa-driver and wpa-conf options in /etc/network/interfaces? I don't see them listed in the interfaces man page?

---

### Post by mback on 2006-07-03
This Worked -- Thanks! \\:D/ 

Now I just have to figure out how to get both Home (WPA) and Work (Open) configurations working smoothly.  Right now my home connection works, but not my work...  I'll have to continue plugging away... and learning.

---

