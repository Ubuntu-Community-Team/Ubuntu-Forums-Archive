---
title: "Belkin F7D1101 install Problem's"
date: 2012-01-21
forum: General Help
---

### Post by Xelator23 on 2012-01-21
Hi guys

It is my first use on Linux (kubuntu 11.10) and i have only an smal problem, so i have install wine on my Netbock but when i will now install the Belkin (Windows driver) i got an Error -1627 when i klick install.

Bus 001 Divice 005: 050d:945a Belkin Coponents


Is it an install part problem or what i do wrong?

---

### Post by sudodus on 2012-01-21
I had a look at the following link
[[COLOR="Red"]_https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") and I found some Belkin devices, but not the one you specify.

It is a known problem, that some wifi device won't work with linux. When you plan to buy a new one, I suggest that you check with that wiki page. But now you have your device so

1. try without any installation at all if it works with the built-in drivers in the linux kernel

2. learn about Ndiswrapper and try that instead of Wine.
[[COLOR="Red"]_https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper_[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

---

### Post by dodle on 2012-02-13
This will probably only help if you are using an older kernel. I compiled a 32 bit version of the driver. It can be found [here](http://sourceforge.net/projects/delugebuilds/files/drivers/rtl8712/). The source is found [here](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true). But, you would probably be better off using Ndiswrapper.

---

