---
title: "Ubuntu 11.04 Running EXTREMLY HOT on Acer laptop"
date: 2011-06-24
forum: General Help
---

### Post by mickyponthenet on 2011-06-24
Hey

Ive been using Ubuntu for about a week now.. i used to use linux alot along time ago, but i switched over to windows to play some games that dont seem to be getting any support from WINE.

But now ive moved back to ubuntu and ive fixed the majority of problems myself apart from one..

I dont know why but when i login to ubuntu, i can hear the fan running pretty much at maximum speed and the bottom of the laptop is extremely hot.. its making me sweat (No kidding).

I checked on system monitor to see what processes are using the CPU, and it appears that no more than 20% of the CPU is being used at any one time, infact System Monitor itself uses more CPU than any other application.

I tried adding some lines to the /etc/modules file to fix the problem, which briefly solved the issue, but its come back?..

I have no idea whats wrong with this laptop, its actually not that old either, i know alot of people are saying "Crack it open and reapply thermal paste" but im positive that is a useless suggestion.

Its running with an AMD processor and an ATI GPU, which ive heard theres not very good support for, but in past  versions of ubuntu, ive had no problems like this at all..

Does anyone have any suggestions?..

I think if it doesnt get resolved within a couple of days, ill be trying to re-install an older version of ubuntu, and if thats still causing problems, ill just resort to a different OS.. i didn't get any of these issues with windows, so im wondering whats up.

Cheers if anyone can help though

---

### Post by mickyponthenet on 2011-06-24
Also i added the following lines to /etc/modules

```

battery
ac
thermal
processor
acpi-cpufreq
cpufreq-userspace

```

It solved the problem for ONE day..

Im using a CPU scaler too, and it doesnt seem to be any use... even now ive just got firefox open and its using maximum CPU usage.. WHAT!?

I know the fan is working too, i can hear it a mile away

---

### Post by mickyponthenet on 2011-06-25
Anyone fancy helping me out?

Xsensors is telling me K10temp is usually at 70c degrees when idling.. it then goes up to 80c degrees when simply browsing the web..

Someone help?

---

### Post by dreKion on 2011-06-26
Hello, I have the same problem with my Acer Aspire 8943G.

Now the temperature is 90ºC

If I can't solve this I will be back to W7 :(

---

