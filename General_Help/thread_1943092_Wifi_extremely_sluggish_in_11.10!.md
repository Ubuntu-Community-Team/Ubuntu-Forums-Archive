---
title: "Wifi extremely sluggish in 11.10!"
date: 2012-03-18
forum: General Help
---

### Post by gfunkera on 2012-03-18
I just installed the newest iteration of Ubuntu (Oneiric) on my ThinkPad W500 Lenovo laptop. Love the operating system. Can't surf the web without the ethernet cable plugged in because the wireless internet is very very very slow.
However, ethernet is normal. Does anyone know the fix? Im used to dealing with b43-fwcutter with laptops that have Broadcom 43xx drivers.

The driver on this laptop is: Intel Corporation Ultimate N WiFi Link 5300

---

### Post by jquis8411 on 2012-03-18
Did you install the intel/ broadcom drivers? If you did uninstall them and use the native ubuntu ones. The proprietary drivers bring my laptop to a crawl with that adapter.

---

### Post by gfunkera on 2012-03-18
Actually, no I did not install the Broadcom drivers. I thought about it but after running lspci, i realized that there was no mention of broadcom drivers anywhere.. see above...

i found a temporary fix. I run these two commands and everything works great but after restarting, the commands must be re-issued:

```
sudo rmmod iwlagn
sudo modprobe iwlagn 11n_disable=1
```

Im still looking for the permanent fix.

---

