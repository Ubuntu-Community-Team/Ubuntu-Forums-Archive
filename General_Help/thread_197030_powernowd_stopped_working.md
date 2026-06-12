---
title: "powernowd stopped working"
date: 2006-06-15
forum: General Help
---

### Post by Ramses de Norre on 2006-06-15
Hmm powernowd stopped working.. It worked fine yesterday and today gkrellm states "n/a MHz" and I get this in terminal: ```
ramses@icarus:~$ sudo /etc/init.d/powernowd start
Password:
 * Starting powernowd...  * CPU frequency scaling not supported
                                   [ ok ]
ramses@icarus:~$ cpufreq-selector 1000000
No cpufreq support

```
I'm using an amd athlon 64 3700+
Any idea whether a module could've been unloaded or where to look for a solution?

---

### Post by yopnono on 2006-06-15
well have had this also. I just uninstalled the powernow and acpid or was it acpi,
and then install them again.

---

### Post by Ramses de Norre on 2006-06-15
I should have tried that.. A reinstall of powernowd fixed it =)

---

