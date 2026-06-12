---
title: "Troubleshooting Emergency Shutdown"
date: 2010-08-25
forum: General Help
---

### Post by dkgi on 2010-08-25
Hi,

I'm new to Ubuntu and have a problem with my laptop. After awaking from sleep, my computer sometimes (I have not yet found a pattern) seems to perform an emergency shutdown (no announcement, it just shuts down, fast, as if you disconnect the battery) after ca. 5 minutes. I'm not really sure what to do here... I've browsed some logs in /var/log without results since I have no Idea what to look for.

Can anyone point me to the right log? Thanks.

Regards,
    Dominik.

---

### Post by cbraxton on 2010-08-25
> **dkgi said:**
> After awaking from sleep, my computer sometimes (I have not yet found a pattern) seems to perform an emergency shutdown (no announcement, it just shuts down, fast, as if you disconnect the battery) after ca. 5 minutes. I'm not really sure what to do here... I've browsed some logs in /var/log without results since I have no Idea what to look for.

This is probably not what you want to hear, but suspend and hibernate are areas that are still rough in Linux. I've learned that rather than spend hours of fruitless debugging it's best just not to use those "features" if they are causing problems. (For that matter I've seen Windows systems that also do not resume properly.)

Suspending and resuming a running system is a decidedly non-trivial task that is fraught with potential problems. Do a full shutdown and power up instead and things will work a lot more smoothly.

---

