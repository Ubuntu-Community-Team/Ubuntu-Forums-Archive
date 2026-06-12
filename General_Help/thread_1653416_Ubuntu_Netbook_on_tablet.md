---
title: "Ubuntu Netbook on tablet"
date: 2010-12-26
forum: General Help
---

### Post by Tappet Head on 2010-12-26
I recently purchased a Pioneer Dream pad L11 HD tablet, Works pretty good with Win7 64 bit, but really need to drop back to 32 bit. I only really ever wanted to run Ubuntu on the Tablet, so I installed 10.10 net book on it, And it runs quite slow, but I cannot get the touch screen to work, If I touch it it goes straight to the upper left corner. I am looking at changing to the desktop edition if the netbook doesn't grow on me.

I was sent a few drivers and etc from my supplier, telling me to pre compile the drivers, I search and search the Internet on how to's, as I have never done it, no luck. Most of the packages that were sent contain info on installing them, I have tried to follow these step buy step, and all I get is E, or invalid in an attempt to install these drivers, but no luck at all. on a good note, the wireless appears to be working great!.

He's the link of the drivers [ftp://service.pioneer.net.au/PUB/Drivers/L11/Linux-Generic/](ftp://service.pioneer.net.au/PUB/Drivers/L11/Linux-Generic/) , would be great if someone with a bit of know how would be able to help me out with this. 


Cheers
TH

---

### Post by stevo56 on 2010-12-28
Tappet Head
I have the same machine and got it working using info from [Green Hughes blog]("http://www.greenhughes.com/content/installing-ubuntu-1010-samsung-nb30-touchscreen-netbook")

I just followed the directions under the touchscreen section on this link, changing only one part as follows;

**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0xeef:0x72a1:0x40"**


These directions worked for me.


Steve

---

### Post by Tappet Head on 2011-06-07
> **stevo56 said:**
> Tappet Head
I have the same machine and got it working using info from [Green Hughes blog]("http://www.greenhughes.com/content/installing-ubuntu-1010-samsung-nb30-touchscreen-netbook")

I just followed the directions under the touchscreen section on this link, changing only one part as follows;

**GRUB_CMDLINE_LINUX_DEFAULT="quiet splash usbhid.quirks=0xeef:0x72a1:0x40"**


These directions worked for me.


Steve

Thanks stevo, it worked a treat.

---

