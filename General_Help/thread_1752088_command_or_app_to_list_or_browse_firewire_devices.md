---
title: "command or app to list or browse firewire devices?"
date: 2011-05-07
forum: General Help
---

### Post by Defrector on 2011-05-07
Is there a terminal command or application to browse attached firewire devices in the likes of lspci and lsusb? I'd like to view elementary device information such as the ID, manufacturer, and the like.

Thanks

---

### Post by Defrector on 2011-07-25
Found something that will do that and a bag-of-chips!

```
grep . /sys/bus/firewire/devices/fw*/*
```

...results in a lot of info about all firewire devices detected on the chain(s). To dumb it down to just name:

```
grep . /sys/bus/firewire/devices/fw*/*_name
```

---

