---
title: "Monitor and secondly control temperature"
date: 2010-07-15
forum: General Help
---

### Post by jlunse on 2010-07-15
In Ubuntu 10.04:

1. I would like to monitor the temperature on parts having sensors. Any idea how?

2. I would also like to control maximum allowed temperature on parts having senors. Any idea how?

I think my fans are making to much noise, running on high speed to often and I just want to allow slightly higher temperature before they start to burst off. But I would first like to monitor temperature and secondly start to tweak sensor limits by increasing allowed temperatures and by doing that, hopefully decrease the operation of some fan's speed - resulting in less noise.

Another idea is to replace fans with more effective once, but I would like to avoid that if possible, since it cost.

---

### Post by jlunse on 2010-07-16
With information from a friend, I managed to monitor CPU temperature in two different ways:

[I][B]cat /proc/acpi/thermal_zone/THRM/temperature

acpi -t[/B][/I]

They both works fine and nicely reports the temperature in degC.

So, I started to monitor CPU temperature and when CPU fan start/stop this unpleasant noise. I found the following:
Fan noise _starts at 65 degC_ and doesn't _stop until it goes under 55 degC_. 

I guess I have two alternatives here: 

1. Find out how to set these _two_ temperature limits and allow higher temperature. Maybe set start to 75 degC and stop to 65 degC. 

**Any idea how I could change these limits? **

2. Add more cooling to avoid CPU temperature above 63 degC?

---

### Post by dcstar on 2010-07-16
> **jlunse said:**
> In Ubuntu 10.04:

1. I would like to monitor the temperature on parts having sensors. Any idea how?

2. I would also like to control maximum allowed temperature on parts having senors. Any idea how?
......

[LIST=1]
[*]Install one of the many monitoring tools like gkrellm etc.
[*]Don't know.
[/LIST]

---

### Post by dino99 on 2010-07-16
gnome-sensors-applet let you know and tweaks every settings about temperaures with icons in the top panel: right click on it to add the temp icons then set the preferences

---

### Post by jlunse on 2010-07-19
Good tips, thanks!:)

I tested gkrellm and it looks nice and gives a lot of information. But I really like the simplicity in **gnome-sensors-applet** and I could now easily monitor temperature in the panel.

However, still I don't know how to control temperature limits. I investigated BIOS and there is no settings there.

But I think the initial problem to all this was actually one of the disks which now crashed (today):(. It seems like temperature dropped a lot (5 to 10 DegC) after removing this dysfunctional device.

---

