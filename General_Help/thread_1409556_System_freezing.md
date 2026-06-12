---
title: "System freezing?"
date: 2010-02-17
forum: General Help
---

### Post by CharlesJWelsh on 2010-02-17
I am beginning to think that this is due to having "Bad Sectors" on my HDD. I AM going to replace it... But I'm curious. What exactly may be causing this? It is an ongoing problem and I cannot seem to fix it. I have re-installed Ubuntu numerous times (re-downloading the ISO every time) I can't seem to put my finger on the cause of this problem. And help would be appreciated.
Regards;
CJ

---

### Post by wojox on 2010-02-17
Have you checked your Log Files?
What exactly happens? Can you move the mouse but not click anything?

---

### Post by CharlesJWelsh on 2010-02-17
Yep, move mose, click, nothin. I end up havin to do that CTRL + A + PrtSc + U + B. And sometimes when it reboots, It freezes before login screen. Just stays black and my HDD light on my laptop doesn't blink. No, I haven't checked logs... I don't know how to.

---

### Post by wojox on 2010-02-17
The first place to look for debug information is /var/log. kern.log, daemon.log, messages and dmesg often contain precious information about what went wrong. This will help you identify which hardware or even software component is causing trouble to the kernel.

In your case it sounds like x-server. Try looking in Xorg.0.log

---

### Post by Ric95 on 2010-02-17
Did you install a video card? 
If so, check your bios to make sure its looking in the right slot for it.
eg: if the card is a PCI-E, make sure the bios point to that, not PCI.
This cause is rare, but it happened to me so I though I'd mention it.

---

### Post by CharlesJWelsh on 2010-02-17
Okay... I have NO idea what I am looking for... I looked through all the logs you detailed and all i see is a bunch of sh** i don't understand.

---

### Post by wojox on 2010-02-17
Open your terminal and run:

```
cat /var/log/Xorg.0.log | grep EE
```

And post it back up here.

---

