---
title: "Any network managers work with WPA?"
date: 2006-01-23
forum: General Help
---

### Post by klepto on 2006-01-23
Sure I can find a signal using commands and connect to it,
and I have written my own scripts to connect to my own network
which uses WPA. It would be nice to boot up my laptop and see a signal
and be able to connect to it with no fuss and it also intergrate with
wpa_supplicant. 

I've heard of gtkwifi and network-manager but both of those require
gnome deps(ugh). Any hope?

---

### Post by mlomker on 2006-01-23
[QUOTE=klepto]I've heard of gtkwifi and network-manager but both of those require gnome deps(ugh). Any hope?[/QUOTE]

Not really.  I've tried all of them that I could find and am also using scripts--in my case by running them out of Whereami.

---

### Post by xtacocorex on 2006-01-23
I got tired of having to manually do this in kwifimanager, so I installed wifi-radar from the repos.

Works really well once you set up the networks you want to use. It automatically connects during boot, it's pretty slick.

---

### Post by Behel on 2006-01-25
I am trying to connect also to the wireless network of my university. I am using wifi-radar but don't know how to set it up to allow a WPA connection. Where do I enter my username and password?

The university provide the following information:
> The following authentication types are currently supported:

    * PEAP (MS-Chap-v2)
    * EAP/TLS

Network Authentication is "Open" or "WPA". It is recommended that you use TKIP rather than WEP encryption if available. AES Encryption is not supported at this time. (coming soon)

For PEAP authentication you will need the Certification Authority certificate to be installed on your client.

Your client can use this to ensure you are connecting to the wireless service. If you have the option to set an "Outer Identity" then set this to your username.

For EAP/TLS authentication you will also need a user certificate.

Then there's a link for two certificates...

In wifi radar, I have to provide a driver for WPA... What's that?

Anyone can help me?? I already suffered enough to get my chinese Netgear WG511v2 wireless card working...

---

### Post by Stealth on 2006-01-25
Wifi radar needs a driver because WPA Supplicant is configured by using a specific one. For instance, I think if you type in ipw, it would get your Intel ProWireless chips (ipw2200,ipw2100) to work. Some others could be mad, or ndis, there should be a manual somewhere for the different codes :)

---

