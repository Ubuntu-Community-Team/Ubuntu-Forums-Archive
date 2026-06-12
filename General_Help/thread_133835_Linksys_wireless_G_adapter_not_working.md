---
title: "Linksys wireless G adapter not working"
date: 2006-02-20
forum: General Help
---

### Post by ImperialHunter904 on 2006-02-20
I just installed ubuntu on my desktop today and I use a linksys wireless G usb adater V4 to connect to the internet normally (I have it on my laptop too, but ubuntu auto detected my built in wireless) . Anyway, nothing happens when I start the comp up with it in, it's in the device manager but theres no wireless connection under networking like there is on my laptop. Now, someone on IRC told me to use ndiswrapper. I used the wiki provided by them to install it. I did ndiswrapper -i [driver inf file] (after installing ndiswrapper), and it said "Installing [file]". Now, I press ndiswrapper -l and it provides me with the driver, it says, "driver present, hardware present" I then pressed ndiswrapper -m and rebooted like I was told too (the person on IRC then had to leave...). Now, I boot up and that little box still isn't showing up by my clock like on my laptop, nor does networking detect a wireless connection. ndiswrapper -l still detects the driver and hardware present though. Any help would mean alot to me, thanks!


edit: I just did sudo lshw -businfo  and the linksys device is coming up as a generic device, shouldn't it be network?

---

### Post by ImperialHunter904 on 2006-02-21
fooled around with IWCONFIG and its still not showing wireless connection in the networking, anyone know how I might fix this?

---

