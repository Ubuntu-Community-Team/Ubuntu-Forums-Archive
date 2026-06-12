---
title: "Wireless problem"
date: 2006-01-25
forum: General Help
---

### Post by Nightmare JG on 2006-01-25
Not sure where to put this, since it started after I installed kubuntu-desktop...
Anyway, my wireless card (a Linksys wusb11 v2.8) worked gret while I was using Gnome, it had to be activated manually everytime I started my computer though.
After I upgraded to KDE it was working fine for about a day then it stoped working.
Research turned up two commands that I can use:
```

sudo iwconfig wlan0 mode Managed essid linksys
sudo dhclient wlan0

```
If I run these everytime I start my computer, my card will enable, otherwise it shows up, but won't enable.
Is there anyway around this? Maybe a script that could run at startup or somthing?

Thanks,
Jacy Gaddis

---

### Post by torx on 2006-01-26
i have the exact problem as you, and have also resorted to the exact solution.

---

