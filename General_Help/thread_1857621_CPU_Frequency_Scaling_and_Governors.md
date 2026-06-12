---
title: "CPU Frequency Scaling and Governors"
date: 2011-10-10
forum: General Help
---

### Post by nogasbiker on 2011-10-10
From reading what I could find and also using gnome's applet, it seems that there are two ways to control cpu speed:

  a) setting a specific clock speed
  b) selecting a governor (conservative, ondemand, performance, powersave)


Is there a way to get a combination of the two?  Specifically, Ondemand with a cap.  I'd like to have the kernel run at the lowest clock speed when nothing is going on, but I also want it to go no higher than a particular clock speed.

For those that might ask "why", I want to minimize power usage, but at the same time get some amount of performance.  A compromise between both.

---

### Post by dcstar on 2011-10-11
> **nogasbiker said:**
> From reading what I could find and also using gnome's applet, it seems that there are two ways to control cpu speed:

  a) setting a specific clock speed
  b) selecting a governor (conservative, ondemand, performance, powersave)


Is there a way to get a combination of the two?  Specifically, Ondemand with a cap.  I'd like to have the kernel run at the lowest clock speed when nothing is going on, but I also want it to go no higher than a particular clock speed.

For those that might ask "why", I want to minimize power usage, but at the same time get some amount of performance.  A compromise between both.

Install the** powernowd** package and see if that can be tweaked.

---

### Post by Asmodai on 2011-10-11
You can use cpufreq-set from the cpufrequtils package to place an upper limit on the frequency for the ondemand governor.
I've set different presets to a number of hotkeys and I'm quite happy with it. That way, I can switch between different modes quickly.

---

### Post by nogasbiker on 2011-10-20
> **Asmodai said:**
> You can use cpufreq-set from the cpufrequtils package to place an upper limit on the frequency for the ondemand governor.
I've set different presets to a number of hotkeys and I'm quite happy with it. That way, I can switch between different modes quickly.Thanks, this worked great, exactly what I needed.

For my machines, the "conservative" governor is useless.  It behaves exactly like OnDemand, instead of raising the cpu cap slowly.  So I modified this governor.

---

### Post by nogasbiker on 2011-10-20
> **Asmodai said:**
> You can use cpufreq-set from the cpufrequtils package to place an upper limit on the frequency for the ondemand governor.cpufreq-set seems to set the max frequency for all governors.  It doesn't seem to change a single governor, is that correct?

I did
```
cpufreq-set --governor conservative --max 1333000
```

When I switched to OnDemand later, it also was capped at 1.3ghz.  So it seems the --max is system wide and not for a particular governor.

---

### Post by jrollf on 2011-12-04
> **dcstar said:**
> Install the** powernowd** package and see if that can be tweaked.

FYI as far as I can tell, **powernowd** is not available in Ubuntu 11.10.  I get the following message:

[I]"Package powernowd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source"[/I]

My Google research seems to support that it isn't available 'yet.'

---

