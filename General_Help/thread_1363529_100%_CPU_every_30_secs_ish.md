---
title: "100% CPU every 30 secs ish"
date: 2009-12-24
forum: General Help
---

### Post by pabc on 2009-12-24
I have a fresh install of 9.10 on a HP 510 laptop. Every 30 seconds or so whatever app i'm using greys out, the cursor stars flashing and gnome-system-monitor shows 100% cpu usage.

However, during the 100% spike I cant see which app is going mental. How can I log what app is using all the cpu cycles if i cant see it through the GSM so I can ditch it

---

### Post by switch10 on 2009-12-24
> **pabc said:**
> I have a fresh install of 9.10 on a HP 510 laptop. Every 30 seconds or so whatever app i'm using greys out, the cursor stars flashing and gnome-system-monitor shows 100% cpu usage.

However, during the 100% spike I cant see which app is going mental. How can I log what app is using all the cpu cycles if i cant see it through the GSM so I can ditch it

Firefox has been known to cause issues like this.  I have never experienced this problem first hand, but I think it might have something to do with add-ons...

---

### Post by fragos on 2009-12-24
Open a terminal window and run top. Use that to see what process takes the CPU while you're performing other tasks like web browsing.

---

### Post by pabc on 2009-12-28
Cheers, I found 'top' during trying to sort this out but it's not responsive during the 100% load.

next time it happens I'll top -p FIREFOX_PID > ~/top.log to see if it is FF playing up. My gut feeling is it's adobe as the problem has only happened when a flash object has been rendering.

---

### Post by fragos on 2009-12-28
Try running the System Monitor-> Resources tab. It will graphically depict CPU use age over a 60 sec period. True their may be a culprit that hits 100% CPU but it might be that your idle state is to high and you need to back off on on overhead like Compiz or unnecessary aps that run in the background. My system will on occasion register 100% but it doesn't become unresponsive like yours does. How much memory in that laptop?

---

### Post by pabc on 2009-12-30
its a HP510 notebook so pentium M and 1GB RAM. I'll check the idle CPU useage and report back.

---

### Post by fragos on 2009-12-30
With 1GB RAM my system almost never uses swap memory. Doubt memory capacity is the issue. My CPU is an AMD Sempron 2800+ at 1.6GHz. My system performs well for most uses.

---

### Post by rnerwein on 2009-12-30
try: chrt 99 top
to figure out the runaway process.
you must be super user to do this. eg. sudo chrt 99 top
chrt - manipulate real-time attributes of a process
be careful with the command chrt - espacally if you have only one cpu !!! :-))

---

