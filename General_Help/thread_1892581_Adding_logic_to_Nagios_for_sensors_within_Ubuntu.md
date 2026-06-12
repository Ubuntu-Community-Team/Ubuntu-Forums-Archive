---
title: "Adding logic to Nagios for sensors within Ubuntu"
date: 2011-12-08
forum: General Help
---

### Post by Digital-Sniper on 2011-12-08
I currently run Nagios on Ubuntu and I am trying to figure out how to add logic to the following scenario:

For example here is my sensors output:

root@ubunag:/usr/local/nagios/etc/keys# sensors -f
via686a-isa-6000
Adapter: ISA adapter
Vcore:       +1.82 V  (min =  +0.06 V, max =  +3.10 V)
in1:         +0.40 V  (min =  +0.06 V, max =  +3.10 V)
+3.3V:       +3.45 V  (min =  +2.98 V, max =  +3.63 V)
+5V:         +4.83 V  (min =  +4.51 V, max =  +5.50 V)
+12V:       +12.72 V  (min = +10.81 V, max = +13.20 V)
fan1:       5578 RPM  (min =    0 RPM, div = 2)  ALARM
fan2:          0 RPM  (min =    0 RPM, div = 2)
temp1:      +110.8Â°F  (high = +295.2Â°F, hyst = -95.6Â°F)
temp2:       +88.9Â°F  (high = +295.2Â°F, hyst = -95.6Â°F)
temp3:       +73.4Â°F  (high =  +4.6Â°F, hyst = +54.5Â°F)  ALARM

Now what I do currently with Nagios is the following command to simply output this information:

define service{
        use                             local-service         ; Name of service template to use
        host_name                       SkunkWerkz
        service_description             SENSORS MB Temperature
        check_command                   mbtemp
        notifications_enabled           0
        }
define command{
        command_name    mbtemp
        command_line    sensors -f | grep 'temp2'
        }

There is no logic to this as its only displaying the output.  What I would like todo is add logic to this to where if the temperature for example runs past a certain range then I get a critical warning, etc etc.

So for example with 'temp2' which is the MB temp I would like it to throw a warning at lets say 100 F and a critical at 120 F for example.

Any help is appreciated in Advance,..:)

---

