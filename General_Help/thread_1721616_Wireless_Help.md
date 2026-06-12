---
title: "Wireless Help"
date: 2011-04-04
forum: General Help
---

### Post by chevmaro on 2011-04-04
I am running Ubuntu 10.10 and having a problem with my wireless card.  It is a WG311v3.  I installed the driver and it works fine until i reboot.  Then it doesnt recognize the wireless card.  I have to open up a terminal and type "sudo modprobe ndiswrapper" and then "iwconfig".  It works right after doing this how do i get it to save the settings for ndiswrapper?

---

### Post by bkratz on 2011-04-04
> **chevmaro said:**
> I am running Ubuntu 10.10 and having a problem with my wireless card.  It is a WG311v3.  I installed the driver and it works fine until i reboot.  Then it doesnt recognize the wireless card.  I have to open up a terminal and type "sudo modprobe ndiswrapper" and then "iwconfig".  It works right after doing this how do i get it to save the settings for ndiswrapper?

Copied from the "Comprehensive ndiswrapper troubleshooting guide"


[COLOR="DarkOrange"]In modern versions of Ubuntu, ndiswrapper is supposed to be loaded automatically at boot. Sometimes for various reasons that fails to happen, however. If this appears to be your problem, run this command:[/COLOR]


```
echo 'ndiswrapper' | sudo tee -a /etc/modules
```

[COLOR="DarkOrange"]and the problem should be resolved. This command tells the system explicitly to load the ndiswrapper module while booting, no matter what.
[/COLOR]

---

