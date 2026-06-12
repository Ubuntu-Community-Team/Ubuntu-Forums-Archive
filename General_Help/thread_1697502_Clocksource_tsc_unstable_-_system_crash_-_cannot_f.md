---
title: "Clocksource tsc unstable - system crash - cannot fix"
date: 2011-02-28
forum: General Help
---

### Post by Ozdemon on 2011-02-28
I have had daily crashes on my 10.10 system.  A check of /var/log/syslog shows
```
kernel: [   91.504029] Clocksource tsc unstable (delta = -311857940 ns)
```

I did some searching and I thought the answer was to replace tsc.  First I checked on the available clocksources.

```
gedit /sys/devices/system/clocksource/clocksource0/available_clocksource

hpet acpi_pm 
```

I changed /etc/default/grub by amending a line to:
```
GRUB_CMDLINE_LINUX="acpi=hpet"
``` I updated grub and rebooted.

I checked on the current clocksource:
```
 gedit /sys/devices/system/clocksource/clocksource0/current_clocksource
hpet 
```


I ensured my BIOS was set to the hpet option.

Now I am still getting the "Clocksource tsc unstable" message.  I don't understand how tsc is still the clocksource.  :confused:

Please can anyone tell me how I solve this problem?

I am on 10.10, kernel 2.6.35-25-generic (32 bit) on an AMD64 6000 dual core

---

### Post by mercraus on 2011-04-06
I'm having the same issue, did you ever find a solution to this problem?

---

### Post by Ozdemon on 2011-04-06
> **mercraus said:**
> I'm having the same issue, did you ever find a solution to this problem?

I tried many, many things, including a clean install of Ubuntu 10.04, running memtest for 16 hours, full HD check and analysis and other tests and configs.

I finally solved the problem by uninstalling Ubuntu and installing PCLinuxOS.  My system is now running perfectly.

Having made the move, I am very happy with PCLOS. The only disadvantage is it's repos are not as comprehensive, but that is also an advantage, because nothing goes into the repo's unless it is safe.

---

### Post by davidmohammed on 2011-04-06
I had the same issue - I found that booting with the "noapic" boot option fixed it for me.

---

### Post by Machiavelli on 2011-08-26
> **Ozdemon said:**
> I finally solved the problem by uninstalling Ubuntu and installing PCLinuxOS.

:lolflag:


I'm having the same problem. This sucks.

---

### Post by dcstar on 2011-08-27
> **Ozdemon said:**
> 
.........
I finally solved the problem by uninstalling Ubuntu and installing PCLinuxOS.  My system is now running perfectly.

Having made the move, I am very happy with PCLOS. The only disadvantage is it's repos are not as comprehensive, **but that is also an advantage, because nothing goes into the repo's unless it is safe.**

So what?, please specify **ANYTHING** that is in the Ubuntu repos that is "not safe".

---

### Post by save2 on 2011-12-04
its a well known issue in Ubuntu since kernel 2.6.32+
people sometime report that editing boot option (in grub.cfg)
to clocksource=hpet (or acpi_pm) :i.e
linux	/boot/vmlinuz-2.6.32-36-generic root=UUID=<somenumbers> ro clocksource=acpi_pm quiet
sometimes help.

if you turn off the BIOS auto-cpu-frequency it will also be solved (but then CPU will be running at full power all the time).

some said that adding a general boot param: noacpi or nohz=off helped.

---

