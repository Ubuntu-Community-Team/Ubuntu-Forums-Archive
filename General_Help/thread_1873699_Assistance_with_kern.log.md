---
title: "Assistance with kern.log"
date: 2011-11-01
forum: General Help
---

### Post by Headfirst on 2011-11-01
Greetings,

Recently I built a linux box that I loaded Ubuntu 11.10 on. This was actually the first desktop I've built on my own. I got the OS installed just fine and it will boot up no problem. The issue I'm coming across is once it's been up and running for a little while it will unexpectedly power down. There are no warning messages or anything along those lines. So my first thought is to check out the logs and see what's going on. I did some research and it seems that kern.log is the log file I want to start with.

I booted up the machine and got this log file along with the kern.log.1 which appears to be the old one. I have a hunch that the issue is with the tower overheating but, I'm looking for some sort of verification that is the problem. I've looked over the kern.log and I'm not getting a lot from it. I was hoping that someone out there with a little more knowledge than myself and a free Tuesday evening would be willing to look over the log file.

I've made kern.log and kern.log.1 both available to be viewed by anyone. Just follow these links..

EDIT: Log links removed no longer applicable.

---

### Post by Headfirst on 2011-11-02
Bump?!

---

### Post by tartalo on 2011-11-02
The command ```
sensors
``` gives you the temperatures if you suspect overheating.

---

### Post by Headfirst on 2011-11-02
> **tartalo said:**
> The command ```
sensors
``` gives you the temperatures if you suspect overheating.

tartalo thank you for the command that was just what I needed! I believe it is very obvious from the following information that overheating is my culprit. I am going to put in a different more powerful fan and hope it is able to keep it cool. As long as I'm sitting on the desktop the temperature stays pretty consistent. The instant I opened Firefox it spiked, guess that's why it's called FIREfox :rolleyes: 

Any thoughts? 

```
rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +177.8°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +177.8°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +80.6°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +80.6°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$
rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +80.6°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +80.6°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.00 V 
in3:          +0.84 V 
in4:          +0.96 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.97 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.39 V 
Vbat:         +3.10 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +136.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.97 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.39 V 
Vbat:         +3.10 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +136.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +80.6°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.42 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2935 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.12 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +138.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +80.6°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.10 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +140.0°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +179.6°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +179.6°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.97 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.41 V 
Vbat:         +3.10 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +140.0°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor

rabbidgoat@CaneServer:~$ sensors -f
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +195.8°F  (high = +186.8°F, crit = +212.0°F)
Core 1:      +195.8°F  (high = +186.8°F, crit = +212.0°F)

f71882fg-isa-0a00
Adapter: ISA adapter
+3.3V:        +3.41 V 
in1:          +1.22 V  (max =  +2.04 V)
in2:          +1.01 V 
in3:          +0.85 V 
in4:          +0.98 V 
in5:          +1.12 V 
in6:          +0.92 V 
3VSB:         +3.42 V 
Vbat:         +3.12 V 
fan1:        2946 RPM
fan2:           0 RPM  ALARM
fan3:           0 RPM  ALARM
fan4:           0 RPM  ALARM
temp1:       +156.2°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp2:        +82.4°F  (high = +185.0°F, hyst = +177.8°F)
                       (crit = +212.0°F, hyst = +204.8°F)  sensor = transistor
temp3:          FAULT  (high = +158.0°F, hyst = +154.4°F)
                       (crit = +185.0°F, hyst = +181.4°F)  sensor = transistor
```

---

### Post by Headfirst on 2011-11-02
If it isn't one thing it's another... I took the box apart and I get to looking at the fan and the heat sync over the CPU and it appears the thermal paste (forgive me I'm not sure the correct term) that goes between the sync and the CPU case is quite worn out and it helps to further explain the overheating. So I guess my next task is to reapply the paste and hopefully that will do the trick.

I'm very new at all of this as I mentioned previously. So any sort of advice is greatly appreciated.

---

### Post by tartalo on 2011-11-04
You might also want to check firefox:
[http://kb.mozillazine.org/Firefox_CPU_usage](http://kb.mozillazine.org/Firefox_CPU_usage)

---

