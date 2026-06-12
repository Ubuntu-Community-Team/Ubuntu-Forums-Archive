---
title: "Ubuntu boots in text mode"
date: 2011-03-22
forum: General Help
---

### Post by andrew1992 on 2011-03-22
Hello, 
I just did a fresh install of Ubuntu 10.10 and after running the Update Manager and restarting, I get the following message upon boot:
```

shpchp 0000:00:01.0: Cannot reserve MMIO region
Too many connections

```
And it only boots into text mode. This seems to be an error in starting the xserver. startx yields the following message:
```

Segmentation fault at address 0xf000e739

Caught signal 11 (Segmentation fault). Server aborting

```

I'm wondering if this is a problem with my video card/driver. From lspci:

```
VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD 4200]
```Any ideas on how to boot back into GUI mode?

---

### Post by cookiecloud on 2011-03-22
ATI... oh noes! >_>

Are you using the free Xorg drivers, or the official ATI ones?

---

### Post by andrew1992 on 2011-03-22
> **cookiecloud said:**
> ATI... oh noes! >_>

Are you using the free Xorg drivers, or the official ATI ones?

I have no clue...I just used the "Additional Drivers" tool before I had this problem to get the driver.

---

### Post by cookiecloud on 2011-03-22
ATI... oh noes! >_>

Are you using the free Xorg drivers, or the official ATI ones?

To (retry) starting the GUI (X server) do:

```
 startx 
```

or

```
 sudo /etc/init.d/gdm restart
```

---

### Post by andrew1992 on 2011-03-22
If this helps any, looking at /etc/X11/xorg.conf tells me that my driver is "fglrx".

---

### Post by andrew1992 on 2011-03-22
startx fails...

---

### Post by cookiecloud on 2011-03-22
I'm sorry, that's where my ATI knowledge drops off - I can only suggest you wait patiently for a reply from someone more adept with this stuff. I wish I could have assisted you - I hate not fixing stuff :(

---

### Post by andrew1992 on 2011-03-22
Haha what luck, it's fixed! I booted in failsafe graphics mode and did a default restoration.

---

### Post by cookiecloud on 2011-03-22
> **andrew1992 said:**
> Haha what luck, it's fixed! I booted in failsafe graphics mode and did a default restoration.

:D

I'm glad to hear that you resolved your problems; it's always immensely satisfying to fix things without needing the help, eh!

:-) 

All the best mate!

CC

---

### Post by DeborahSu on 2011-03-23
Mine did the same thing, but ONLY after the most recent kernel update.  Up until then, it was just fine.  And when it goes to sleep at night or while I'm at work, it won't wake up in the morning without a reboot, (text) restore, reboot and start.  Guess I'll try the failsafe graphics mode restore and see if that fixes it more permanently.

---

