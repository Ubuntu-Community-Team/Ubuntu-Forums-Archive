---
title: "Suspect overheating, where to look?"
date: 2010-01-28
forum: General Help
---

### Post by LightLink on 2010-01-28
I'm using ubuntu 9.10 on a dell inspiron laptop, I came home from work today and it was off. I suspect overheating, would there be some error message in the logs, and if so where would I find it and what would it say?

---

### Post by JackRock on 2010-01-28
Open up your case, and check for dust.  Use canned air and a non-static vacuum to get rid of any dust.  Focus heavily on any and all fans you can reach.  Install extra fans, if possible.  Close up any open slots in the back of the machine.

---

### Post by Overcast32 on 2010-01-28
You could also start it up, jump into the BIOS and see if it has any 'hardware monitoring' menu item - leave it run for a while and watch the heat. There may also be some 'hardware monitor' software out there for Linux, I know there is for Wind'ers.

If you do clean it up, might want to take the fan off the heatsink if you can and clean the heatsink really good.

---

### Post by LightLink on 2010-01-29
Jan 28 18:48:08 mageta-laptop kernel: [15933.318620] Critical temperature reached (96 C), shutting down.

Well there it is, the sad thing is I only had electric sheep screensaver going, reaching temps of 96 seems absurd unless the screensaver is just that big of a resource hog. 

I want to go buy some canned air and maybe some thermal paste before I take it apart, this is what I am dealing with:

[http://support.dell.com/support/edocs/systems/ins1525/en/SM/cpucool.htm#wp1179839](http://support.dell.com/support/edocs/systems/ins1525/en/SM/cpucool.htm#wp1179839)

Also I read about undervolting the cpu and was considering it, does anyone ever done this before?

---

### Post by cascade9 on 2010-01-29
96C with a screensaver? o.O Ouch. 

I could be that your video card is producing a lot of the heat, in some cases a screensaver will be running the video card under enough loading to matter. If you change it to 'blank screen' that might help..but you shouldnt be hitting 96C even with a loaded video card. 

Hopefully the can of air, a good blow out and replacing the thermal paste will fix things.  

> **LightLink said:**
> Also I read about undervolting the cpu and was considering it, does anyone ever done this before?

I've ran an undervolted (and mildly overclocked) CPU for years, and never had any issues from it. 

That was a desktop though, I've never even tried with a laptop.

---

### Post by audiomick on 2010-01-29
> **cascade9 said:**
> ... and replacing the thermal paste will fix things.  

I would be looking most closely at that, and then that all the fans are really running. If it is getting that hot, it means the heat isn't getting drawn out of the component, i.e. a heat sink has lost conductive contact with it's component, or a fan has stopped, or both.

---

### Post by doas777 on 2010-01-29
> **Overcast32 said:**
> You could also start it up, jump into the BIOS and see if it has any 'hardware monitoring' menu item - leave it run for a while and watch the heat. There may also be some 'hardware monitor' software out there for Linux, I know there is for Wind'ers.

If you do clean it up, might want to take the fan off the heatsink if you can and clean the heatsink really good.


usually bios level thermal monitoring is not recomended, as the bios load phase of boot is one of the hottest. that is because the more advanced power managment subsystems are not yet online. at work we use safeboot, and that causes the same issue. when we remotely reboot a pc overnight, on the way back up, it stops at safeboot (waiting for user authentication) and really heats the sucker up.

---

### Post by mr clark25 on 2010-01-29
you might try lm-sensors. it works great for me.
```

sudo apt-get install lm-sensors
sudo sensors-detect

```

there are some more steps to it that i find hard to explain here, so here is a link to a youtube video that i made some time ago: [http://www.youtube.com/watch?v=kaVcWtraWAs](http://www.youtube.com/watch?v=kaVcWtraWAs)

it should work. could you post the output back here?


weather or not you can undervolt will depend on if the option is available in your motherboard's bios.
if you do want to undervolt, make sure your cpu os still stable with prime95. (or you could try my pi stress test)

prime 95 will need to be ran with wine.

---

### Post by LightLink on 2010-01-29
acpitz-virtual-0
Adapter: Virtual device
temp1:       +47.0°C  (crit = +85.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +85.0°C, crit = +85.0°C)  

Typing in "sensors" in the terminal yields these results. All I have running is pidgin instant messenger and firefox.

---

### Post by doas777 on 2010-01-29
> **LightLink said:**
> acpitz-virtual-0
Adapter: Virtual device
temp1:       +47.0°C  (crit = +85.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +47.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +47.0°C  (high = +85.0°C, crit = +85.0°C)  

Typing in "sensors" in the terminal yields these results. All I have running is pidgin instant messenger and firefox.

those are all reasonable temps for a cpu (you have an athalon don't you), if you believe them. it does worry me a little that they all output deg though. I've never had 2 differant sensors produce the same result with any regularity. theres usually at least a 5 deg differance between cores.

---

