---
title: "Ubuntu 9.04 Alternate Install Mystery"
date: 2010-03-01
forum: General Help
---

### Post by HugoB on 2010-03-01
Hi Everyone

I came across an interesting scenario over the weekend and would like to know if anyone else have encountered the same scenario as well before.

I took out an Ubuntu 9.04 alternate install disc over the weekend and wanted to perform an install of it onto a legacy machine. The first idea was to try and install a command-based system, but when the disc booted, it didn't give me any command based install option, unless it was a live cd (but it would be hard to believe).

After the above attempt failed, a program called unetbootin for windows was found that could actually upload the original copy of the Ubuntu 9.04 alternate install onto a flash drive and boot with it when the computer started up. I then performed the previous mentioned and great it was possible to boot from the flash drive when the computer started up. 

The copy that was put onto the flash drive, ironically provided the option to perform a command-based install. After choosing the option, the install steps proceeded normally until it reached a point where I had to start downloading packages from the internet. The strange thing is just that these packages already existed on the flash drive and I couldn't see why it was necessary for the Ubuntu install to connect to the internet to download the software if it was already located on the original install on the flash drive.

Any comments for the above mentioned would be appreciated.

Thank you

---

### Post by C.S.Cameron on 2010-03-01
The only time I have ever had a Live USB try to connect to the internet during an install was when using mini.iso.
9.04 Live CD should have it's own tool, (usb-creator), for making a Live USB.
Some people prefer UNetbootin and some prefer usb-creator.

---

### Post by dcstar on 2010-03-02
> **HugoB said:**
> 
........
The copy that was put onto the flash drive, ironically provided the option to perform a command-based install. After choosing the option, the install steps proceeded normally until it reached a point where I had to start downloading packages from the internet. The strange thing is just that these packages already existed on the flash drive and I couldn't see why it was necessary for the Ubuntu install to connect to the internet to download the software if it was already located on the original install on the flash drive.


Every install downloads **updated** packaged from the Internet (if it can).

---

### Post by HugoB on 2010-03-03
Hi everyone

Thank you for the suggestions, I would like to try some of it over the weekend

---

