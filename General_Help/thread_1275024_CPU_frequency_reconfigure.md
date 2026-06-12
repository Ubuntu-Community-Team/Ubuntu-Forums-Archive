---
title: "CPU frequency reconfigure"
date: 2009-09-25
forum: General Help
---

### Post by arnab_das on 2009-09-25
I tried to do it with the "sudo dpkg-reconfigure gnome-applets" command, and then "Should cpufreq-selector run with root privileges?" question was asked, i selected "yes". then i added the cpu frequency scaling monitor and found that there was an error saying  i couldnt configure my processor settings. i am using AMD Sempron 3200+.

What I want to know is how do i change to the deafult CPU frequency settings? Do I type "sudo dpkg-reconfigure gnome-applets" and then select "No" to root privileges? Is that the default settings?

---

### Post by trundlenut on 2009-09-25
Is the option to allow the OS change the processor speed enabled in the BIOS of the machine?

Is it a laptop and is acpi enabled?

---

### Post by arnab_das on 2009-09-25
its not a laptop. its a pc. just wanted to make sure my processor was using the max processing capability.

what do i do to the " sudo dpkg-reconfigure gnome-applets" permissions btw, change it to "No"?

---

### Post by trundlenut on 2009-09-25
Ubuntu should be able to control the speed of the processor so that it uses the full power when needed and drop the speed and therefore power used at other times.

A look [here]("http://en.wikipedia.org/wiki/List_of_AMD_Sempron_microprocessors") suggests that there are several different versions of the sempron 3200+ and not all of them seem to have the cpu throttling capabilities (Cool'n'Quiet).  You need to work out exactly what model you have I think.

Run the following in a terminal and see what it comes back with.
```
cat /proc/cpuinfo
```

---

### Post by dcstar on 2009-09-26
> **arnab_das said:**
> 
.........
what do i do to the " sudo dpkg-reconfigure gnome-applets" permissions btw, change it to "No"?

Just don't select it.

---

