---
title: "Check CPU and GPU Temp"
date: 2010-08-27
forum: General Help
---

### Post by Vexiphne on 2010-08-27
Does anyone know of a program to ubuntu that checks CPU and GPU temprature?

---

### Post by dcstar on 2010-08-27
> **Vexiphne said:**
> Does anyone know of a program to ubuntu that checks CPU and GPU temprature?

```
man sensors
```

---

### Post by Vexiphne on 2010-08-27
I'm a newbie and that was a little bit to hard for me to understand :) Isn't there like a simple program with a gui out there?

---

### Post by pro511 on 2010-08-27
Applications >>System>>System monitor
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167619&stc=1&d=1282901561[/IMG]

:D

---

### Post by Daniel0108 on 2010-08-27
> **pro511 said:**
> Applications >>System>>System monitor
For Ubuntu 10.04 Lucid Lynx, its on: System>>Administration>>System monitor ;)
But I don't see a temprature here...
It's just the usage...
PS:
Go to  /proc/acpi/thermal_zone/
with your file browser...
Then go into one of the folders, which name's starting with TH thats the CPU temperature...
Or you write "sudo apt-get install lm-sensors" into the terminal...
That is a gui.. but I haven't tested it yet.. so, I dunno if it works :D
EDIT: I found a second program, where you don't need any kernel dependencies :P 
just write "sudo apt-get install xmbmon" into a terminal :D
Here is a picture of xmbmon:
[IMG]http://www.linux-user.de/ausgabe/2004/02/056-xmbmon/xmbmon.png[/IMG]
Yours,
Daniel

---

### Post by wojox on 2010-08-27
I haven't used it in sometime, but Conky is a good system monitor.

---

### Post by Vexiphne on 2010-08-27
Thank you all for your help :D

---

