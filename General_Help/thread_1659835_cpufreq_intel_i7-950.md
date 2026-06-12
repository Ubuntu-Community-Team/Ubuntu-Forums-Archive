---
title: "cpufreq intel i7-950"
date: 2011-01-04
forum: General Help
---

### Post by carolinason on 2011-01-04
i am running an intel i7-950 and trying to get kubuntu to use each core has been frustrating.

i used cpufreq-set to set to perfomance, but it seems to do nothing. even though i see in cpuinfo that cpu0 is set to the full freq.

kubuntu 10.10 seems to only want to use cpu2(in system monitor) or cpu1 in cpuinfo. i mean it will use other cores, but only to a small %. 

i've searched on this most the day and can't get seem to get any further.

i have no problem with each core being throttled, but only one core seems to be used.

thanks

---

### Post by carolinason on 2011-01-04
well i guess i spoke to soon. things seems to be looking okay now. i think my mistake was using 7zip as an indicator. i was under the impression it was threaded. leave it to a flash video to show me all cores seem to be 'sharing' the load.

not sure if cpufreq is the reason. i set it to ondemand.

---

### Post by ean5533 on 2011-01-04
Another good program to test would be the [latest development release of HandBrake]("https://edge.launchpad.net/~stebbins/+archive/handbrake-releases"). I know from using it that it is multithreaded, so try encoding a few videos and see if your processor activity shoots up.

---

### Post by carolinason on 2011-01-04
i've been meaning to try handbrake, i do have a need for it. i'll post results.

thanks ean5533

---

### Post by carolinason on 2011-01-06
i see why they call it handbrake.  i'll need to replace the stock cooler if i want to do things like that. handbrake woke up every core a little too well.

---

### Post by ean5533 on 2011-01-06
At least now you know that your processor isn't going to waste :-)

I think there's a setting somewhere in handbrake to limit CPU utilization if needed, though I might be making that up. You can always underclock your CPU until you get a new cooler if you're truly afraid of damaging the CPU.

Cheers.

---

### Post by carolinason on 2011-01-06
seems my cooler wasn't quite fastened. i removed, cleaned, re-greased and remounted it. all is lovely. thanks for the tips!

---

