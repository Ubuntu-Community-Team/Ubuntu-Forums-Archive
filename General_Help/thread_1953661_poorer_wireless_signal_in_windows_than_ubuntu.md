---
title: "poorer wireless signal in windows than ubuntu?"
date: 2012-04-06
forum: General Help
---

### Post by lightsaberlesbian on 2012-04-06
I've noticed when trying to connect to certain hotspots with weaker signal quality i'm better able to capture those signals on windows than ubuntu.  does anyone relate to this? could it be a driver issue?

---

### Post by idoitprone on 2012-04-06
> **lightsaberlesbian said:**
> I've noticed when trying to connect to certain hotspots with weaker signal quality i'm better able to capture those signals on windows than ubuntu.  does anyone relate to this? could it be a driver issue?

i just here asking some basic information. i not exactly able to diagnose your problem
so? based on your title, windows have worse wifi quality than ubuntu? Or it is the other way around?

```
uname -a
lspci -nnk
```what type of network are you accessing?

n -band?
g -band?

---

### Post by lightsaberlesbian on 2012-04-06
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1483]
    Kernel driver in use: brcmsmac
    Kernel modules: wl, bcma, brcmsmac

3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

does that clarify anything?

---

### Post by wildmanne39 on 2012-04-06
Hi, I think you will get a better connection if you remove the other 2 drivers that are conflicting with the one you need.

Please do:
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Then reboot.
Thanks

---

### Post by lightsaberlesbian on 2012-04-07
Thanks.  I hope this works.

---

### Post by wildmanne39 on 2012-04-07
Hi, please let us know either way and if it does mark the thread solved by using the thread tools at the top of the page.
Thanks

---

### Post by jim_deadlock on 2012-04-07
I've read articles before that suggest the "signal strength" is totally arbitrary and meaningless. You're either connected or you're not.

---

### Post by lightsaberlesbian on 2012-04-07
the thing is i WONT be connected at all when in fact during Windows I will be connected, albeit with "low signal strength."

---

### Post by wildmanne39 on 2012-04-07
Hi, if you are still having trouble please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
If you get closer can you still connect after you made the changes I suggested?
Thanks

---

### Post by lightsaberlesbian on 2012-04-08
I'm surprised.  I think the blacklisting did the trick.  Thanks!

---

### Post by wildmanne39 on 2012-04-08
Hi, that is great, I thought it would most of the time when you have 2 or more conflicting drivers you can not even connect so you were lucky there.
Enjoy

---

