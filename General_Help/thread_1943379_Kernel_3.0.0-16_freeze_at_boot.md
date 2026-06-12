---
title: "Kernel 3.0.0-16 freeze at boot"
date: 2012-03-19
forum: General Help
---

### Post by Hawk__0 on 2012-03-19
I think around the bluetooth loading stage of things it freezes.  If I hit ctrl+alt+del it proceeds to shut down properly, but the only way I can get my computer to boot again is by using kernel 3.0.0-12.

What gives?

---

### Post by TeoBigusGeekus on 2012-03-19
Have you tried blacklisting bluetooth (if you don't need it that is)?

---

### Post by Hawk__0 on 2012-03-19
I don't need bluetooth.  How do I blacklist it? I was going to uninstall it but it looked like apt was going to uninstall a bunch of stuff I did need, that was unrelated for whatever reason.

---

### Post by TeoBigusGeekus on 2012-03-19
I don't know how it's done in Ubuntu, but you could try this;
```
gksu gedit /etc/modprobe.d/blacklist-bluetooth.conf
```
Add
```
blacklist bluetooth
```
Save. Reboot. Post back.

---

### Post by 2F4U on 2012-03-19
It should be sufficient to create, for example, /etc/modprobe.d/blacklist.conf and add the following lines to it

```
blacklist rfcomm 
blacklist bnep 
blacklist btusb 
blacklist bluetooth
```

---

### Post by Hawk__0 on 2012-03-19
Both of these didn't work.  When the purple screen locks up for a lengthy amount of time, it drops to the shell and is stuck on seemingly different processes each boot, but as soon as I hit ctrl+alt+del it still says "Stopping bluetooth..."

---

### Post by TeoBigusGeekus on 2012-03-19
Well then, the only thing I can suggest is to boot with the older kernel and see if any update will fix that.

---

