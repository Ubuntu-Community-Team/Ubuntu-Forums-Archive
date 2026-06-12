---
title: "Detecting Monitor Resolution Settings"
date: 2011-11-18
forum: General Help
---

### Post by cmnorton on 2011-11-18
Does a command -- like xrandr -- exist that would query my Acer 19" monitor to see what modes it supports?

Also, would someone point me to a list of commands to configure my Acer to accept greater than 1024x768?

Thanks.
cmn

---

### Post by dcstar on 2011-11-19
> **cmnorton said:**
> Does a command -- like xrandr -- exist that would query my Acer 19" monitor to see what modes it supports?


Look in the /var/logs/xorg.0.log file.

---

### Post by cmnorton on 2011-11-19
Thanks for answering. I promise to answer this when I get back to work.

---

### Post by cmnorton on 2011-11-28
> **dcstar said:**
> Look in the /var/logs/xorg.0.log file.
Could not find this directory on 10.04.

---

### Post by cmnorton on 2011-11-28
All available resolutions started displaying as soon as I got a more up-to-date KVM. Problem solved.

---

