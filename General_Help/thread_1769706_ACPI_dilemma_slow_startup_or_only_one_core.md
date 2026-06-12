---
title: "ACPI dilemma: slow startup or only one core?"
date: 2011-05-28
forum: General Help
---

### Post by yugo4k on 2011-05-28
I have ubuntu 10.04 installed but need 11.04 also because of my hp scanner (lucid solutions for it didn't work for me and I sort of skipped 10.10). Long story short, I'm having problems with ACPI and natty, specifically concerning startup time (from grub screen to login screen) and the number of cpu cores working.

1- ACPI enabled:
    - lucid works as it should, the 4 cores working and startup under 20s;
    - natty takes about 3min to startup, unless after a while I push the power button making it startup in the usual time (but if I don't wait at least 5s, the computer powers down... I guess that's very unhealthy).

2- ACPI disabled:
    - lucid works with only one core, I checked gnome system monitor, /proc/cpuinfo and "top";
    - the same in natty, only one core working according to the 3 mentioned above.

I've seen both these problems discussed in various threads, but have been unable to find solutions to any of them other than changing the ACPI from "Enabled" to "Disabled" and vice-versa.

If there's already a solution somewhere or if this is the wrong place to post my problem, please let me know. :rolleyes:

Anyways, any help is **really** appreciated. :)

---

### Post by Matt__ on 2011-05-28
I cant help you with your cores problem but surely its easier to try and resolve the scanner issue than totally upgrade for one peripheral device? and all the aditional problems it causes.

What HP scanner.

HP are usually very good with linux as the the HPLIP packages are, to the best of my knowledge, run by current/former hp employees.

in 10.04 update HPLIP
```
sudo add-apt-repository ppa:hplip-isv/ppa 
sudo apt-get update
sudo apt-get install hplip
```and just use simple scan/xsane.

---

### Post by jramshu on 2011-05-28
If you go with only one core you may experience "freezes" due to high cpu usage while using a browser running flash.

---

