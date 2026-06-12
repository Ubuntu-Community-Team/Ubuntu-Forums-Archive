---
title: "Controlling heat, ACPI settings?"
date: 2009-09-02
forum: General Help
---

### Post by nowhere@cox.net on 2009-09-02
Hey all,

I've had a couple incidents now with 9.04 and severe heating issues, the worst being with GnomeDO pegging the CPU usage to 100% and allowing the hottest temps I've ever seen on my laptop. Luckily I was watching and killed it. 

The other issue is with VirtualBox during USB 2.0 transfers. CPU utilization goes very high and the temps get pretty high. 

Anyway, I have changed my bios settings on my T61 on AC power from Performance to Balanced (only two choices) and installed the Freq scaling applet on the gnome panel along with sensors-applet to watch. The new bios setting helped a bit in that the temps stay a bit lower now than before but I still need to test with a long transfer to see what they creep up to. The scaling is definitely jumping back a forth from max to min. 

I found the /proc/apci/thermal_zone/THM0 and THM1 folders and see the trip_points files.  The THM0/trip_points file has only a critical 127°C setting. ```
critial (S5):     100 C
```
The TMH1/trip_points has this:
```
critial (S5):     100 C
passive:           96 C: tc1=5 tc2=4 tsp=600 devices=CPU0 CPU1
```

Questions: (bet you thought I wouldn't get there!)
[LIST]
[*]Is there some documentation on this file?
[*]Is it pulled from bios settings or if I change them will they take effect?
[*]Why have two folders if the settings are jammed into one? 
[*]CPU0 always seems to run hotter than CPU1 which I always wrote off as position on the chip relative to the heat flow. Maybe the settings in THM1 have an effect on CPU1 and not CPU0?
[/LIST]  

Let me know if anyone has any insight...
Thanks!

---

### Post by BitJunkie on 2009-09-02
I had heat/fan problems on my Toshiba L505 laptop. I added the acpi_osi="Linux" parameter in grub's menu.lst (e.g. .... ro quiet splash vga=791 acpi_osi="Linux") and that helped my heat problem. I know this doesn't answer your questions, but it might be something to try.

---

### Post by nowhere@cox.net on 2009-11-20
My solution was to turn OFF Nested Paging. It was the source of all my high CPU usage with Vbox and thus the heat problems.

Word of warning: The GPU + 2 cores CPU can overwhelm the cooling capacity of a Lenovo T61 even if it's nice and clean...

---

