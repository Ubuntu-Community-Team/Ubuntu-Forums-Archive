---
title: "laptop heats up very easily"
date: 2011-03-21
forum: General Help
---

### Post by kolo-01 on 2011-03-21
hi,

i have a toshiba laptop about 2 years old, it has served me well and although it has a few problems i like it, but the issue i want to adress here is now is how rapidly the temperature fluctuates from about 60 degrees c straight up to 95-100 c in the space of less than 2 minutes, i know this is crazy and bad. It comes from running a youtube video or a flash game in google chrome, but obviously the more going on the quicker it heats, i am just asking if there is something that can be done to limit the heating, i am probably going to get one of those mats, but if there is any program available that could help then i would love to know which options there are..
the laptop has not (that i can remember) ever shut down from overheating, but the speed is affected quite badly when hot, any help appreciated

---

### Post by pqwoerituytrueiwoq on 2011-03-21
gksudo gedit /etc/init.d/ondemand
change line 27 
from
```
echo -n ondemand > $CPUFREQ
```to
```
echo -n conservative > $CPUFREQ
```that should help some
you can change the current setting using the CPU Frequency Scaling Monitor Applet
is it full of dust?

i do use a mat myself shaves 13 degrees F off of idle even more for the hdd

---

### Post by arvevans on 2011-03-21
Go to Synaptic Package Manager and do a search for "toshiba".  You will find a number of BIOS interfaces and extension software packages that let Linux software control the Toshiba cooling fan.

If you have a cat, you may need to remove cat hair from the cooling fan.  Some Toshiba laptops are apparently allergic to cats!  :p

---

### Post by ramjet_1953 on 2011-03-21
Might be worth getting out your vacuum cleaner, plug the hose into the blower output, put the fine nozzle onto the hose and then back-flush your CPU cooler outlet.

Often you will see quite a bit of crud blown out of the cooling channel.

Regards,
Roger

---

### Post by Dark_Stang on 2011-03-21
> **ramjet_1953 said:**
> Might be worth getting out your vacuum cleaner, plug the hose into the blower output, put the fine nozzle onto the hose and then back-flush your CPU cooler outlet.

Often you will see quite a bit of crud blown out of the cooling channel.

Regards,
Roger

Be EXTREMELY careful with this, good vacuum cleaners may be too powerful and can cause the fans to spin at very high speeds. I would recommend just using some compressed air (the cans, or from a dry air compressor limited to 15-20 psi).

---

### Post by ex_isp on 2011-03-22
> **Dark_Stang said:**
> Be EXTREMELY careful with this, good vacuum cleaners may be too powerful and can cause the fans to spin at very high speeds. I would recommend just using some compressed air (the cans, or from a dry air compressor limited to 15-20 psi).

Best answer here!

---

### Post by cmileto on 2011-03-22
Can you hear the fans running when its on? Could be a problem where the fan speed control wasnt set up or detected correctly. Wish I could help more. Try searching these forums for acpi. Im thinking along the lines of the HP laptops that had issue like this. See thread here perhaps can be of use:
[http://ubuntuforums.org/showthread.php?t=1709127](http://ubuntuforums.org/showthread.php?t=1709127)

---

