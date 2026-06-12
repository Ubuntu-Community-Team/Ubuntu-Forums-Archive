---
title: "Dapper running Gnome won't shut down"
date: 2006-06-19
forum: General Help
---

### Post by SDREnate on 2006-06-19
When I try to shut down, the last message is "Will Now Halt". Then nothing happens. I did a search and found that some installed apps change some acpi settings. How can I fix this?

---

### Post by niels_r on 2006-06-21
This is the same problem I have after switching to Dapper. With Breezy I didn't had this problem. I also think it has something to do with ACPI support. My motherboard is an Asus AI P5GDC Deluxe. If someone knows how to fix this problem, I would be very thankfull.


Also:

This morning, my PC turned itself off because the CPU overheating protection. The heatsink appeared to be full with dust (after less than 1,5 year!) and after removing the dust everything works fine again. Now I would like to monitor the CPU's temperature (just to be sure...), but this doesn't work. I installed the Gnome 'Computer Temperature Monitor' applet. This applet gives the message: *"There is not Thermal Monitor support on your machine!!!"*. The /proc/acpi/thermal_zone directory is also empty. This seems an ACPI problem to me too. I don't know if this worked with Breezy, because I generally don't care about such things (a system just has to work; also the reason for switching to Ubuntu! :wink:)


By the way; this is my first post here! I am a Ubuntu user since February (I like it very much!) and this is the first problem I encounter.

---

### Post by SDREnate on 2006-06-24
Bump. This happened after I upgraded my kernel. Is it a bug? Anyone?

---

