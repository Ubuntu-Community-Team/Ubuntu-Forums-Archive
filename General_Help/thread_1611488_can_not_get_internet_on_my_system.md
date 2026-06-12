---
title: "can not get internet on my system"
date: 2010-11-01
forum: General Help
---

### Post by idi_htd on 2010-11-01
i just installed ubuntu and i think it does not recognize the ethernet port, i can't download the driver for it since i don't have internet on ubuntu. I have a compaq presario S6300NX; the motherboard is A7V8X-LA motherboard. Can anyone help me with drivers for this so i can download it on my XP and then install them on ubuntu? Or can anyone help me get internet some other way, i tried that option about going to admin, system, networking and entering the static ip or choosing DHCP and i couldnt get it to work. I have ubuntu 10.4; i'm using a DSL modem. That's all, thank you. Also i didnt know where to post for absolute beginner. Now i found it, but i can't move this to it so i apologise for that.

---

### Post by Bitrate on 2010-11-01
That motherboard uses the VT6103 LAN PHY LAN chipset which appears to be supported by Ubuntu. Have you checked that your LAN port is enabled in your systems BIOS ?

---

### Post by idi_htd on 2010-11-02
Yeah the LAN port is enabled. Idk why it does not work, after i log into ubuntu those lines that show if you're connected to the internet blink, as if they're looking for the internet but then it says something like "wired network disconnected, you are now offline"

---

### Post by drdos2006 on 2010-11-02
You might be having issues with IPv6. Check this out, maybe.

[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

regards

---

### Post by bhospadaruk on 2010-12-15
I have a VB7001 motherboard which has a VT6103 wired lan.  It also doesn't work since at least 10.04.  I noticed a lan "driver" on the VIA site that I might try for 10.04:
[http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=60&CatID=3760&SubCatID=127]("http://www.viaarena.com/displaydrivers.aspx?PageID=1&OSID=60&CatID=3760&SubCatID=127")

---

