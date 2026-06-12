---
title: "cpufreq doesn't do anything"
date: 2009-08-21
forum: General Help
---

### Post by insane_alien on 2009-08-21
So, i'm trying to enable the little gnome applet that allows you to select a governer for frequency control. 

i know this is supported on my hardware as i was using it on arch yesterday before my harddrive died. 

i have the applications installed and the applet on the panel but it does nothing and i can't find any documentation relating to how to install it. all the stuff i've seen from googling is about stuff you can do AFTER you get it working.

little help would be appreciated. i'm running 64-bit if it helps.

EDIT: so 've done some more snooping and apparently i don't have any of the kernel modules required (acpi-cpufreq and all the cpufreq_<governor> ones)

what package would these be in? i have the cpufreqd and cpufreq-utils packages installed.

---

### Post by s3MA00RRNY on 2009-08-22
If you don't have those modules, you're probably using the wrong kernel. Go into synaptic and check the installed version. Post it here.

---

### Post by matthewbpt on 2009-08-22
Are you running hardy? (As your profile says) I would recommend changing to Jaunty or Intrepid, I remember having trouble with the Frequency Scaling applet in hardy because it needs root permissions to change the frequencies and the way to give it root permissions was very roundabout, not very straightforward, while in Intrepid and Jaunty it worked immediately.

---

### Post by insane_alien on 2009-08-22
it was the standard jaunty kernel from a fresh install. my profile says hardy because i haven't updated it in ages.

i've decided to abandon my return to ubuntu. i've changed my way of doing stuff too much.

---

