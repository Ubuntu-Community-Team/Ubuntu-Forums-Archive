---
title: "Ubuntu Boot Screen not showing up"
date: 2011-04-30
forum: General Help
---

### Post by rasfl3 on 2011-04-30
Hello. I installed Ubuntu 11.04 on one of my computers which has an NVIDIA graphics card. The Ubuntu Boot Screen doesn't show up. I know this was a problem in 10.10 but I had found a script to fix it which had worked in that version but when I ran it in 11.04, it didn't do anything. I appreciate any help received with this issue. Thank You!

---

### Post by adhika on 2011-04-30
Try this, when booting, select the recovery mode and load with minimal graphics (or something like that).

I saw you are using NVidia, the "current" driver is not working. I revert back to version 173. Otherwise, use:

```
gksudo gedit /etc/X11/xorg.conf
```

And edit the driver name from "nvidia" to "nv"

That should give you a temporary fix. At least that's what I did.

---

### Post by rasfl3 on 2011-05-03
Hi. I noticed that current version wasn't working so I did revert back to Version 173. I did use what you stated above and the driver name is not stated. I just see default device.

Here's what I am seeing:

```


Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection



```

Thanks again for your help.

---

### Post by rasfl3 on 2011-05-08
bump

---

### Post by rasfl3 on 2011-05-30
Does anyone have a solution for this yet?

---

