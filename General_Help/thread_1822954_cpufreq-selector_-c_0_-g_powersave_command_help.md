---
title: "cpufreq-selector -c 0 -g powersave command help"
date: 2011-08-11
forum: General Help
---

### Post by dan0804smith on 2011-08-11
when ever i type int his command i do it twice because i have two cores to it looks like this:

cpufreq-selector -c 0 -g powersave cpufreq-selector -c 1 -g powersave


when ever i type this it says that "you must be root"  what does thsi mean

---

### Post by Kira_Belka on 2011-08-11
it means you have to do it or as root .. or using sudo

---

### Post by TBABill on 2011-08-11
Are you trying to actually set the governor with this action? I've never used cpufreq-selector before, but I often use cpufreq-info and cpufreq-set. The man page for cpufreq-selector seems to be very similar to cpufreq-set.
 
When I try to set my governor, I generally: ```
sudo cpufreq-set -c 0 -g ondemand
``` or whatever I choose to set it to. Then I do the same for each subsequent CPU.
 
I think your error is only that, as stated by Kira_Belka, you didn't precede the command in the terminal by sudo to give you root permissions.

---

### Post by Kira_Belka on 2011-08-11
Also ... Cpu frequency Monitor applet is rather comfortable thing :P

---

