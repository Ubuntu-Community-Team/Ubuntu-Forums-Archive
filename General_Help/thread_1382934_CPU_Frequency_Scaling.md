---
title: "CPU Frequency Scaling"
date: 2010-01-16
forum: General Help
---

### Post by LithiumHelios on 2010-01-16
Hi,

I'm having a problem with the CPU frequency scaling. It was working fine in Jaunty but broke after the upgrade to Karmic. Not come across any solutions that seem to work. Any one have any experience with problems along these lines? Any help would be fantastic.

Thanks!

---

### Post by wojox on 2010-01-16
Try running:

```
sudo modprobe p4_clockmod
```

which should return nothing. Then add:

```
p4_clockmod
``` 

to your 

```
gksudo gedit /etc/modules
```

to ensure the CPU clock scaling module starts with the system. Now, to add the CPU frequency scaling monitor applet to the panel.

---

### Post by LithiumHelios on 2010-01-16
Hi thanks for the reply.

Running 
```
sudo modprobe p4_clockmod
```

returns

> WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.save, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.

Though i'm not sure what Alsa has to do with this?

---

### Post by LithiumHelios on 2010-01-16
Should also mention that the above method didn't seem to fix the problem. The frequency monitor has been added to the panel but is showing incorrect values and won't scale at all. It's odd because it was working in Jaunty fine.

---

### Post by LithiumHelios on 2010-01-17
Anyone have any further ideas?

---

