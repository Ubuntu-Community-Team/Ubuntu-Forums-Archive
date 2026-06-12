---
title: "Battery not recognised?"
date: 2010-06-18
forum: General Help
---

### Post by FrontalNoize on 2010-06-18
Hi,

I've just installed 10.04 and everything seemed to work fine.  I am running it on a Q-Force laptop.  

The moment I removed the electricity plug though, my laptop shut down in less than 5 seconds.  I'm guessing my battery isn't fully recognised.  

When I check the power management menu under battery, I get all information.  Status = fully_charged.  

Any idea what could cause this?

---

### Post by FrontalNoize on 2010-06-19
anyone?

---

### Post by Matt Brooks on 2010-06-21
i have the same problem. i read somewhere that you can add this line to your /etc/modules file 

sudo modprobe pmu_battery

---

### Post by The2DQuartet on 2010-07-11
> **Matt Brooks said:**
> i have the same problem. i read somewhere that you can add this line to your /etc/modules file 

sudo modprobe pmu_battery

Before I give this a try, do you have any background information on this, such as where you read it, if it works, drawbacks, etc?

Also, */etc/modules* lists kernel modules to be loaded at boot time so I would expect you just add 'pmu_battery' to the list without the modprobe command?

---

