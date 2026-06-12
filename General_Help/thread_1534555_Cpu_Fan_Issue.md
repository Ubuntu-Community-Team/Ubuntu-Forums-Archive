---
title: "Cpu Fan Issue"
date: 2010-07-19
forum: General Help
---

### Post by bonowantbiddy on 2010-07-19
I have just recently install ubuntu 10.04, Dual booted with windows 7.
In Ubuntu it seems like that the system is reading my processor fan as the main fan in my computer because in ubuntu the fan is almost screaming speed and slows down constantly variating. but in windows 7 it is at a whisper speed. This is the first time i have had this problem and not sure how to fix it. 


Ubuntu 10.04 running on a E-machine et-1831-05

---

### Post by ubunterooster on 2010-07-19
try ```
sudo apt-get install thinkfan
```[quote=thinkfan]Some hardware has a kind of broken fan-control and lets the fan run
faster than really needed. Thinkfan will prevent this by controlling
the fan on its own (the fan speed for each temerature interval can be
adjusted in the configuration file).

Thinkfan supports most hardware trough the generic sysfs hwmon interface.
It also supports the Thinkpad-specific thinkpad_acpi interface.[/quote]

---

