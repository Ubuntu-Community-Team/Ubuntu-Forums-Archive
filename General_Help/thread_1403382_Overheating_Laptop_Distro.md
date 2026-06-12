---
title: "Overheating Laptop Distro?"
date: 2010-02-10
forum: General Help
---

### Post by Turnips on 2010-02-10
I have a W7J and it overheats like mad, usually I use windows but I have tried xubuntu but it seems to overheat and the fan goes really loud a lot of the time; it wasnt as bad with xubuntu with some configurations but its still too loud.  I'm looking for a linux distro that wont use as much processor, and maybe not spin the hard drive as much. But I still want to be able to customize my task bar and open videos and stuff really easy within the internet browser.  I also dont want a non-windows style taskbar like crunchbang or antix  

Is there anything good for me to try?  I appreciate any advice this thing is loud, even with new thermal paste put into it.  Thanks!

---

### Post by shriramrs31 on 2010-02-10
overheating laptops is usualy a sign of something faulty in hardware, so you dont need to look for less cpu hogging OS. Because eventually the problem will get worse and your computer will shut off frequently from overheating. I am assuming here ofcourse that this overheating of your laptop is a recent phenomenon (i.e) your laptop was not always like this.

Dust accumalation in the CPU fan, proper contact between heatsink and processor with agood quality silicon paste and in worst case faulty processor.

If your laptop has always been like this, then u are already in good hands with xubuntu. Perfect compromise between eyecandy, userfriendliness and performance.

You can also try some of the lighter customisable distributions like archlinux.

---

### Post by Turnips on 2010-02-10
Well it has always been like this, but I like to use it in class and stuff and it gets really freaken loud.  I replaced the thermal pads with new arctic silver ceramique already and the fans clean.

Thanks for the arch suggestion however I cant get access to the internet to install arch linux since I only have wireless, plus I'm not very good at it.  I had done some configurations with xubuntu and it did reduce the heat by a lot but I was hoping there might be something similar but for a more minimalist users.

---

### Post by Nunu on 2010-02-10
Hve you had the machine running Linux all along? some laptops run hot when ACPI and the OS conflicts or not managed properly by the OS. I know of some laptops that you had to disable ACPI for it to boot the live CD.

---

### Post by shriramrs31 on 2010-02-10
Okay, you have to give arch linux a try definitely. It might pay off ;-)

Also What helped me with my old laptop was replacing the fan with a newer quieter model.

If you search enough, you can find a slimmer, better, quieter model of fan that fits within the space in your laptop.

Good luck ;-)

---

### Post by shriramrs31 on 2010-02-10
Also as nunu suggested, have a look if the power management settings are in order. For example CPU Temperature monitoring and fan speed control (If your laptop supports it). 

have a look in "/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies" to see if your laptop supports cpu frequency scaling. If so, you can limit your cpu frequency to the minimum possible to prevent overheating.

---

### Post by Nunu on 2010-02-10
> **shriramrs31 said:**
> Also as nunu suggested, have a look if the power management settings are in order. For example CPU Temperature monitoring and fan speed control (If your laptop supports it). 

have a look in "/sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies" to see if your laptop supports cpu frequency scaling. If so, you can limit your cpu frequency to the minimum possible to prevent overheating.

Good one. Also have a look at you BIOS and see if there are any Performance/Battery balancing tools that are turned off or on. 

Some machines does it though the BIOS others hands it to the OS.

---

