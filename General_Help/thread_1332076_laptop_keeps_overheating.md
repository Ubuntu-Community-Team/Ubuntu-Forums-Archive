---
title: "laptop keeps overheating"
date: 2009-11-19
forum: General Help
---

### Post by malachiislame on 2009-11-19
i recently installed  9.10 and know my laptop over heats in an hour or so... so when i used windows i could set my computer in a power saver mode that slowed my processor that made it run a littel less hot. is there anything i can do in ubuntu that could do something similar. sorry if this is stupid question

---

### Post by Windows Nerd on 2009-11-20
It is normal for a laptop to get hot, but not after only an hour. What surface do you have your laptop on? If it is a cloth or fabric the laptop may not have enough air flow to allow its fans to pump the heat out. A month ago now on the local news where I live a guy apparently had his laptop catch on fire because he left if on the couch. Try to put your laptop on a desk or hard surface to allow the fans to not get blocked. 

There is a power saving option in Ubuntu, but this may not always prevent your  computer from overheating.

Scott

---

### Post by undecim on 2009-11-20
It could be one a few things causing this:

1: As Windows Nerd mentioned, your laptop may not be getting enough airflow. Make sure you're not blocking the fan vent.

2: Some program may be using a lot of your CPU, causing your CPU to run at full speed. Take a look at the programs in your system monitor (make sure you have "All Processes" selected from the View menu). Click "% CPU" above the list to sort programs by CPU usage, and find what programs are using the most.

3: There may be dust or dirt collecting on or around your CPU fan and vent. This can hard to fix on a laptop, but you may be able to take a memory or hard drive panel off the bottom of you laptop to use some canned air on your CPU fan. (I have to do this about once per month, because my cat's like to sit against my warm laptop and somehow manage to fill up the vent with hair)

---

### Post by Groszman on 2009-11-26
also watch here:
[http://ubuntuforums.org/showthread.php?t=1315065&page=3](http://ubuntuforums.org/showthread.php?t=1315065&page=3)

---

### Post by Onesimus on 2009-11-26
It might be helpful if you gave us some information about the Make and Model of your laptop.  I have a Dell, that requires me to install software to properly control the fans.

---

### Post by blueridgedog on 2009-11-26
CPU scaling on your laptop may not be working.  What is the output of the following command:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
``` 

If it sates "performance", then that is your issue, but let's see what it states before we jump to conclusions.

Also, if you are running system monitor, it is resource intensive and will actually cause the problem you speak of, so it is best to only run it when you want to, versus leaving it running in the panel all the time.

---

### Post by malachiislame on 2009-12-03
> **blueridgedog said:**
> CPU scaling on your laptop may not be working.  What is the output of the following command:

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```If it sates "performance", then that is your issue, but let's see what it states before we jump to conclusions.

Also, if you are running system monitor, it is resource intensive and will actually cause the problem you speak of, so it is best to only run it when you want to, versus leaving it running in the panel all the time.


it says on demand

---

### Post by malachiislame on 2009-12-03
> **Onesimus said:**
> It might be helpful if you gave us some information about the Make and Model of your laptop.  I have a Dell, that requires me to install software to properly control the fans.

i have a gateway t series running a dual amd turion64

---

