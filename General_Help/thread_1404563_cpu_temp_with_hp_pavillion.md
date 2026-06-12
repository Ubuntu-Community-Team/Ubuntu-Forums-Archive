---
title: "cpu temp with hp pavillion?"
date: 2010-02-11
forum: General Help
---

### Post by princeofnam on 2010-02-11
I want to see my CPU's temp on my top application panel, but after I installed Computer Temperature Monitor there's a huge X with the caption, "No Thermal Monitor Support!"  Any ideas?

---

### Post by Mark Phelps on 2010-02-11
Don't know how Computer Temperature Monitor works, but other solutions read thermal sensors in your machine.

If you haven't already, install lm-sensors from synaptic.

Once that is installed, open a terminal and enter "sudo sensors-detect" and reply Yes to all the questions.

At the end, it will update your config to allow sensor monitoring.

After that, reboot, open a terminal, and enter "sensors".  If the sensors were detected, and the correct kernel modules identified and loaded, you should see a list of settings -- temps, voltages, etc.

If you see nothing, it means that the kernel modules don't exist to use the hardware sensors on your machine.

---

### Post by undecim on 2010-02-11
I'm running an HP TouchSmart and have yet to get any temperature readings.

---

### Post by princeofnam on 2010-02-11
Thanks Phelps. Those instructions were excellent.

---

