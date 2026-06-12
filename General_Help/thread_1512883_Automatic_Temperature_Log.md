---
title: "Automatic Temperature Log"
date: 2010-06-18
forum: General Help
---

### Post by JBA2337 on 2010-06-18
I need to record the temperatures in my computer in a log file that I can look at later. Are there any temperature monitoring programs that will automatically generate a log of the temperatures? I need a program that will record date, time, and temperatures at a selected interval. 

Thanks.

JBA2337

---

### Post by stoneage on 2010-06-18
I think sensord will allow you to do that:-
[http://packages.ubuntu.com/lucid/sensord](http://packages.ubuntu.com/lucid/sensord)

It is installable via synaptic or terminal.

---

### Post by JBA2337 on 2010-06-18
To stoneage:

Thank you very much! I had been looking all over for a program that logs temperatures, and I could not find what I needed through Google. Sensord does exactly what I wanted.

It logs the data to the system log. I can easily view this log by looking at /var/log/syslog or by running ksystemlog. This shows me the log of temperature readings that I can look at whenever I want to.

JBA2337

---

