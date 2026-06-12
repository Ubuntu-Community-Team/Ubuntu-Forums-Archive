---
title: "MPlayer install failed - how to repair?"
date: 2010-08-01
forum: General Help
---

### Post by NutmegCT on 2010-08-01
I tried installing MPlayer from Ubuntu Software Center on my 10.4 laptop.

After the install remained stuck at about 50% for 30 minutes, I found that Ubuntu had locked up (pointer moved around, but desktop wouldn't respond), and I had to force the laptop to quit by holding down the power button.

Restarted, tried the same MPlayer install, but got the message about the previous install had failed, and "must be repaired" before trying installation again.

Could someone please show me how to repair a failed install?

Thanks.
Tom in CT

---

### Post by Smart Viking on 2010-08-01
What happens if you run this command?

```
sudo apt-get remove gnome-mplayer && sudo apt-get install gnome-mplayer
```

---

### Post by NutmegCT on 2010-08-01
Worked perfectly!  Thanks.

Tom in CT

> **Smart Viking said:**
> What happens if you run this command?

```
sudo apt-get remove gnome-mplayer && sudo apt-get install gnome-mplayer
```

---

