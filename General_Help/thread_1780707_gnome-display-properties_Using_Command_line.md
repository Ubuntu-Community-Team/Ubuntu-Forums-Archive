---
title: "gnome-display-properties Using Command line?"
date: 2011-06-12
forum: General Help
---

### Post by Master_Ne0 on 2011-06-12
Hi can anyone point me in the right direction to set my monitor settings using the command line?

After upgrading the driver for my display doesn't seem to support the dual screen, i know that it works in mirror mode so i need to be able to change the settings for gnome-display-properties via the command line to get my GUI working again.

Thanks.

---

### Post by Master_Ne0 on 2011-07-11
Edit this file

```
sudo nano ~/.config/monitors.xml
```

To fix the specific issue i had, edit the clone setting to yes

E.G.

```
<clone>yes</clone>
```

---

### Post by Habitual on 2011-07-11
+1 for finding and fixing that. :)

---

