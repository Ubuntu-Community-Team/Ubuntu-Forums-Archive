---
title: "Restore xorg files"
date: 2010-10-13
forum: General Help
---

### Post by Wakawakamush on 2010-10-13
Hi,

I messed up my xorg file and now my pc wont start, when i boot ubuntu the display tells me that there is no input.

---

### Post by mikewhatever on 2010-10-13
Try booting in recovery mode. Xserver is not started in recovery mode, so that it's a CLI environment. If successful, you'll be presented with a list of options, select 'root shell'.
Now reconfigure xserver:

```
dpkg-reconfigure xserver-xorg
```

then reboot

```
reboot
```

---

