---
title: "Ubuntu does not support  WiFi SMC2835w"
date: 2006-02-22
forum: General Help
---

### Post by steel_lady on 2006-02-22
I have a Compaq laptop and I want to put a new linux distribution (RH Enterprise doesn't soport half of my components). So far, I like Ubuntu most but still it doesn't support my Wifi pcmcia card (SMC2835w). Is there a chance that a next version will support it and how long should I wait?

---

### Post by javierfh on 2006-06-16
Hello,

did you ever managed to make it work? I have same card and i would like to use it with Dapper.

Thanks and i hope you can give some help if you managed.

Javi

---

### Post by mozetti on 2006-06-16
I had a SMC2632W WiFi-B (atmel chipset) card that worked fine in Breezy, but when I did a dist-upgrade from Breezy->Dapper it stopped working. I tried a little to get it to work, but I also had a Linksys WPC54G card (Broadcom 43xx chipset) that I was able to get working easily using ndiswrapper. So, I never tried too hard to get the SMC card to work.  Just putting this up here in case our SMC cards used the same chipset, so you know that I *did* have problems with it in Dapper even though it worked out of the box with Breezy.

---

### Post by javierfh on 2006-06-16
[QUOTE=mozetti]I had a SMC2632W WiFi-B (atmel chipset) card that worked fine in Breezy, but when I did a dist-upgrade from Breezy->Dapper it stopped working. I tried a little to get it to work, but I also had a Linksys WPC54G card (Broadcom 43xx chipset) that I was able to get working easily using ndiswrapper. So, I never tried too hard to get the SMC card to work.  Just putting this up here in case our SMC cards used the same chipset, so you know that I *did* have problems with it in Dapper even though it worked out of the box with Breezy.[/QUOTE]

Hi,

thanks for the reply, i wish someone has managed to make it work and can give some hints or help to make it work.
I only have that card and would like to make it work, its a pity because it works fine with XP ..so lets see if anyone knows some trick.

Let me know or post here if you find something out.

Javi

---

### Post by jchiso on 2006-07-25
I had been using this card in Breezy along with gtk-wifi.  After updating to Dapper it would not connect.  I checked to see if the required firmware file had been copied in the new installation but it was not there.  I went back and placed the "isl3890" file into the /lib/hotplug/firmware directory as it had been before, rebooted and now it connects.  I had to go back into the Network settings and activate the wireless interface and set up the security settings and adjust the preferences on the Wireless Connection Manager.

A few folks had pointed out the info on the "isl3890" in earlier posts, so do a search if you need some background.

---

### Post by kaede on 2007-04-20
just wan't to know more about isl3890. anyone know where to find it?

does it really solve the problem for smc2835?

---

