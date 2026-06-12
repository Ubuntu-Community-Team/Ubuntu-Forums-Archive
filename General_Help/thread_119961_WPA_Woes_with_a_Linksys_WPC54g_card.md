---
title: "WPA Woes with a Linksys WPC54g card"
date: 2006-01-20
forum: General Help
---

### Post by strazzere on 2006-01-20
Hey gang,

Basicly I've only recently started to use Ubuntu for a couple of days, however it's not my first distro - so I'd say I'm fairly decent at trying to get most *nix stuff to work.

I've been searching the forums and googling for a little bit, and not found much about my specific problem. Basicly I've installed Breezy Badger, and got my card configured properly, open access points and WEP. "Basic" WPA seems to be working, however I can seem to get my school/work access point to work.

The specs for connection to the WPA ap are as follows;
WPA/TKIP and encryption of EAP/PEAP with MSCHAPv2

*Normally* on a windozes computer (with a supported wireless) card, it asks for a username and a password. On Mac's and some PDA's we use a certificate, however still enter the username and password (the certificate replaces the MSCHAPv2 i believe).

Now I've been able to hack around with the configurations on the mac's, pda's and windoze boxes, but this linux is tripping me up.

This is what my wpa_supplicant.conf file is;

```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
	ssid="UM-IT-BG"
	ke_mgmt=WPA-EAP
	eap=PEAP
	identity="Timothy_Strazzere"
	password="mypassword"
	ca_cert="/etc/cert/IT.cer"
	phase1="peaplabel=1"
	phase2="auth=MSCHAPV2"
	priority=10
}


```

That was the configuration off of the wpa_supplicant site that made the most sense to me? I guess I need to add TKIP in there, but would that be the pairwise or the group?

Sorry, I'm just a little confused on this whole things. Thanks in advance for any help!

---

### Post by strazzere on 2006-01-20
Not to be pushy, but maybe I should reword some stuff I guess.

Has anyone used wpa_supplicant and gotten it to work?

I've been playing around for the last hour or so with not much luck. I can get it to work with BASIC settings at my house on my own router.

Any one ever used the tool other than me? Any hints?

---

### Post by Maggot on 2006-01-20
Although this isn't related to your card, I did this and got my ipw2200 card working:

[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wpa+ipw2200](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wpa+ipw2200)

I think I had to run a utility for my password that converted it from ASCII to Hex ?  Sorry cannot remember, I just know my password in wpa_supplicant.conf in long alpha-numeric.

Here is my wpa_supplicant.conf:

```
Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

### Associate with any open access point
###  Scans/ESSID changes can be done with wpa_cli
network={
       ssid="my-ssid"
       scan_ssid=1
       proto=WPA2
       key_mgmt=WPA-PSK
       psk=long-string-of-crap
}

```

---

### Post by Maggot on 2006-01-20
Remembered the command :) 

wpa_passphrase YourSSID YourPassword

outputs info you throw in wpa_supplicant.conf

After I did that, it worked.

---

### Post by strazzere on 2006-01-20
[QUOTE=Maggot]Remembered the command :) 

wpa_passphrase YourSSID YourPassword

outputs info you throw in wpa_supplicant.conf

After I did that, it worked.[/QUOTE]


Maggot,

Thanks man, but I've tried that. The deal is your using WPA-PSK (PreShared Key).

I need to be using WPA-TKIP - EAP/PEAP w/ MSCHAPv2.

I don't have a PreShared Key I can enter, however that is correct information you gave me and does with with the WPA-PSK networks I've tried.

Thanks for the valiant effort and trying to help. I guess I need someone whose used the nasty settings for WPA_Supplicant

---

