---
title: "Check Current Video Driver Version?"
date: 2009-07-07
forum: General Help
---

### Post by biriachan on 2009-07-07
How can I found out more information on the current Video driver in use on a system?

---

### Post by Megrimn on 2009-07-07
You could figure out what driver you are using, then open synaptic and do a search for the driver name.  it should display that information if it is in there.

---

### Post by biriachan on 2009-07-07
> **Megrimn said:**
> You could figure out what driver you are using, then open synaptic and do a search for the driver name.  it should display that information if it is in there.



Any sugesstions on  how to figure out what driver I'm using?

I want to be able to detect which video driver / kernel module is in use on any given ubuntu desktop.


There has to be a simple terminal command to find this information....

---

### Post by biriachan on 2009-07-08
My system has a ATI 4350 on ubuntu 9.04, and is running on the open source drivers (No closed ATI or Ubuntu packages are installed).

I would like to find a Terminal command that will let me view the current video module/driver in use with xorg.

;)

---

### Post by biriachan on 2009-07-09
A very nice person over at linuxforums pointed me to "/var/log/Xorg.0.log"


Which had just what I was looking for....


LoadModule: "radeon" 

Loading /usr/lib/xorg/modules/drivers//radeon_drv.so

---

