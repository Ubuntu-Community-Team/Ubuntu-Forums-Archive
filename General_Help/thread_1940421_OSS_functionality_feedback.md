---
title: "OSS functionality? feedback?"
date: 2012-03-13
forum: General Help
---

### Post by princeofnam on 2012-03-13
I've been trying to install the drivers for my Toneport converter. [http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html](http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html)

One of the instructions is > 
Only use the OSS drivers for native [[COLOR=darkgreen]OS[/COLOR][COLOR=darkgreen] [/COLOR][COLOR=darkgreen]support[/COLOR]]("http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html#") and to prevent feedback while using Jack Keep the “Monitor” channel muted.

I looked into Sound Settings and don't see any of the options available that allow me to switch to "OSS drivers" or to keep the "monitor" channel muted.

---

### Post by idoitprone on 2012-03-13
> **princeofnam said:**
> I've been trying to install the drivers for my Toneport converter. [http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html](http://www.ubuntugeek.com/how-to-install-a-line6-guitarport-or-toneport-ux1-or-gx.html)

One of the instructions is 

I looked into Sound Settings and don't see any of the options available that allow me to switch to "OSS drivers" or to keep the "monitor" channel muted.

if it is using jack api, then your use alsa driver stack
[http://www.opensound.com/wiki/index.php/Building_OSSv4_from_source](http://www.opensound.com/wiki/index.php/Building_OSSv4_from_source)
[https://help.ubuntu.com/community/What%20is%20JACK]("https://help.ubuntu.com/community/What%20is%20JACK")

here documentation on jack and oss is becoming deprecated, much to my distaste

if you want ossv4 then you have to do alot of times to get it installed

[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#JACK](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#JACK)

---

