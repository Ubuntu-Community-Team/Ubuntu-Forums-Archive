---
title: "Setting Volume On Startup"
date: 2010-09-25
forum: General Help
---

### Post by Lancelot59 on 2010-09-25
I have an issue with my machine. The volume is 100% on startup, and I need that fixed. 

I looked around and found [THIS]("http://stackoverflow.com/questions/414894/set-ubuntu-sound-volume-on-boot") on stackoverflow. However I cannot find the rc-default file I need to edit to make that solution work. I'm running Karmic. Anyone else find a solution to this problem?

---

### Post by foxmulder881 on 2010-09-25
Just change to volume manually and it should stay the same upon reboot unless otherwise changed.

---

### Post by Lancelot59 on 2010-09-25
> **foxmulder881 said:**
> Just change to volume manually and it should stay the same upon reboot unless otherwise changed. How do I go about doing that?

---

### Post by foxmulder881 on 2010-09-25
> **Lancelot59 said:**
> How do I go about doing that?

Just click on the volume icon in your panel and change to the desired volume. This should be the remembered setting upon each reboot unless it's otherwise changed by you.

---

### Post by Lancelot59 on 2010-09-25
> **foxmulder881 said:**
> Just click on the volume icon in your panel and change to the desired volume. This should be the remembered setting upon each reboot unless it's otherwise changed by you.
The problem is that it isn't remembered. The settings don't load till I login.

---

### Post by foxmulder881 on 2010-09-27
> **Lancelot59 said:**
> The problem is that it isn't remembered. The settings don't load till I login.

Of course they don't. How else would the system know what setting to use if you haven't logged in yet?

---

### Post by Lancelot59 on 2010-09-27
> **foxmulder881 said:**
> Of course they don't. How else would the system know what setting to use if you haven't logged in yet?
Hence my problem. I want to adjust the systems defaults so that it doesn't blow my ears off when it turns on.

---

### Post by foxmulder881 on 2010-09-27
> **Lancelot59 said:**
> Hence my problem. I want to adjust the systems defaults so that it doesn't blow my ears off when it turns on.

Just disable the startup sound. Assuming that's what you're talking about.

---

### Post by WorMzy on 2010-09-27
Get them to your preferred settings, then open a terminal and run:

```
sudo alsactl store
```

This should create a file called asound.state inside /etc, which keeps a copy of your current alsa settings and should be read by Ubuntu when the system starts up.

---

### Post by Lancelot59 on 2010-09-27
Didn't work. Startup noise still blares.

---

