---
title: "How to make PowerTOP changes persistant across suspend/reboot?"
date: 2012-05-14
forum: General Help
---

### Post by Helios747 on 2012-05-14
Hello,

I'm running Ubuntu 12.04 x64 on my ASUS notebook. I've installed PowerTOP to maximize my battery life with the OS, and it works great!

However, some of the changes PowerTOP makes don't stick. Things such as "VM writeback timeout" and SATA link PM don't like to stay activated/tweaked after I suspend or reboot.

Is there a way to make it persistent? Or a list of the changes PowerTOP likes to make so I can just throw it in rc.local?

---

### Post by Helios747 on 2012-05-16
bumpity

---

### Post by 2F4U on 2012-05-16
PowerTop has no functionality to make these changes persistent. You need to find the appropriate settings and do the configuration on yourself.

---

### Post by Helios747 on 2012-05-16
Yeahhhh, that's what I was thinking.


Looks like I'll start hunting down what each change is. I wish it showed me the command instead of "Good/bad"

Well thank you!

---

### Post by screaminj3sus on 2012-07-03
I know this thread is a teeny bit old, but I've figured this out in case anyone is wondering, you can achieve this using pm utils.

Sata ALPM can be enabled with this command (taken from here: [https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks):](https://wiki.ubuntu.com/Kernel/PowerManagement/PowerSavingTweaks):) ```
echo SATA_ALPM_ENABLE=true | sudo tee /etc/pm/config.d/sata_alpm
```

For vm_writeback I've added the following script to /etc/pm/power.d (you also need to make it executable before it will work)
```
#!/bin/sh
case "$1" in
    true)
       # Less VM disk activity. Suggested by powertop
        echo 1500 > /proc/sys/vm/dirty_writeback_centisecs
    ;;
    false)
       #Return settings to default on AC power
        echo 500 > /proc/sys/vm/dirty_writeback_centisecs
    ;;
esac

exit 0

```

and for nmi_watchdog I've added the following script to /etc/pm/power.d:
```
#!/bin/sh

case $1 in
  true)
 
    # Running on battery
 
    # Disable the NMI watchdog
    echo 0 > /proc/sys/kernel/watchdog
 
  ;;
  false)
 
    # Running on charger
 
    # Enable the NMI watchdog
    echo 1 > /proc/sys/kernel/watchdog
 
  ;;
esac
exit 0

```

---

