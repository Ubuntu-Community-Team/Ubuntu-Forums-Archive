---
title: "How can I Log system events?"
date: 2012-06-05
forum: General Help
---

### Post by WBMachinery on 2012-06-05
I want to create a script that tells me the exact duration of the battery (I don't find the battery level indicator very exact). 

 One of the parameters for my script is knowing the time when the system is turned on and off, so I can calculate the exact time of operation. 

 So my question is how can I log the time when the system is turned on and off?

 Also if somebody could point me out to a program or script that already does that I would appreciate it.

---

### Post by matt_symes on 2012-06-05
Hi

If your happy with minute granularity, then how about some thing really simple like running this in a terminal (or a script) at start up.

```
watch -n 1 uptime > time_up
```

At next boot 

```
cat time_up
```

will tell you the uptime.

How in exact are you finding the battery applet ?

Kind regards

---

### Post by WBMachinery on 2012-06-05
Well at 100% it says it lasts 8 or 9 hours, sometimes it even says its 10 hours. Then it drops down from those values to 3 or 4 hours (it does this in less than an hour) then goes back up,and it just fluctuates a lot,witch I understand but I need to know the exact time as to configure my system as best as possible. 

Thanks for the help on the command.

---

### Post by matt_symes on 2012-06-06
Hi

Can you post you script so far ? It will give us a better idea of what you are trying to achieve.

You can hook into the battery events.

```
matthew@matthew-Aspire-7540 ~ % cat !$
cat /etc/acpi/events/battery
# /etc/acpi/events/battery
# Called when AC power goes away and we switch to battery

event=battery
action=/etc/acpi/power.sh
matthew@matthew-Aspire-7540 ~ 
```

It is easy to get the date/time using the date function.

```
matthew@matthew-Aspire-7540 ~ % date +"%D %H %m %S"            
06/06/12 13 06 41
matthew@matthew-Aspire-7540 ~ % 
```

Read the man page for date to get the options.

If you are interested then the battery charge information is avaliable under

```
/sys/class/power_supply/
```

On my system

```
matthew@matthew-Aspire-7540 ~ % ls /sys/class/power_supply/BAT0 
alarm        charge_full_design  current_now  device        model_name  present        status     technology  uevent              voltage_now
charge_full  charge_now          cycle_count  manufacturer  power       serial_number  subsystem  type        voltage_min_design
matthew@matthew-Aspire-7540 ~ %
```

Hopefully these pointers will help.

Kind regards

---

### Post by WBMachinery on 2012-06-06
Thank you for your help, I've found logs containing valuable information about the charging and discharging times.

```
var/lib/upower
```

With this, and with the power supply directory you pointed me to, I think I'll be able to write the script.Once again thanks for the help.

---

