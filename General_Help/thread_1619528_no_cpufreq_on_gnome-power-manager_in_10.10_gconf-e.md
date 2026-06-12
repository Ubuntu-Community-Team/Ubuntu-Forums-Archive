---
title: "no cpufreq on gnome-power-manager in 10.10 gconf-editor"
date: 2010-11-11
forum: General Help
---

### Post by Niccola on 2010-11-11
Guys, I have a big problem

Usually in Debian the changes about cpu scaling or power management was made in gconf-editor /apps/gnome-power-manager/cpufreq and your respective policies of battery and ac adapter.

But, now I have 10.10 installed in my laptop ECS U50SA with Core2Duo T5750 and juts havent the head cpufreq in gnome-power-manager.

I want to set up a config to when removes the ac adapter, the cpu scaling change to ondemand (for battery time extends). So, how add cpufreq policies in gonf-editor gnome-power-manager? 

regards

---

### Post by Niccola on 2010-11-12
upping!
anyone?

---

### Post by mc4man on 2010-11-12
Don't see where you can adjust that in gconf 
The default now would be to use ondemand  on both ac & battery

Is there some reason you don't want to use ondemand when on ac?
(I found the default value for the up threshold to be unsuitable here - after adjusting, ondemand works quite well and is preferable to any other 'mode'

---

### Post by motonnerd on 2010-11-14
Bump.  I'm searching for a way to make Ubuntu ignore FAH (which has a 'nice' process status)

---

