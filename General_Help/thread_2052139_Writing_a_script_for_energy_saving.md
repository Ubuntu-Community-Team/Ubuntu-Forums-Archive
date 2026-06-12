---
title: "Writing a script for energy saving"
date: 2012-09-02
forum: General Help
---

### Post by kobras on 2012-09-02
Hi!

I have read one article about things which I can make for longer live of my computer on battery.

Two of them should be done always when a system starts(disabling one video adapter and bluetooth):
```

echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
rfkill block bluetooth

```
And then a lot of things which should be switched on when my notebook is connected to power:
```

echo 0 > /proc/sys/vm/laptop_mode
echo max_perfomance > /sys/class/scsi_host/host0/link_power_management_policy
echo max_perfomance > /sys/class/scsi_host/host1/link_power_management_policy
echo max_perfomance > /sys/class/scsi_host/host2/link_power_management_policy
echo max_perfomance > /sys/class/scsi_host/host3/link_power_management_policy
echo max_perfomance > /sys/class/scsi_host/host4/link_power_management_policy
echo max_perfomance > /sys/class/scsi_host/host5/link_power_management_policy
echo ondemand > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
echo ondemand > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo ondemand > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor 
echo ondemand > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
echo 0 > /sys/devices/system/cpu/sched_mc_power_savings
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
modprobe uvcvideo
echo 10 > /proc/sys/vm/dirty_ratio
echo 5 > /proc/sys/vm/dirty_background_ratio
echo 6000 > /proc/sys/vm/dirty_writeback_centisecs

```

and switched off when working on battery:
```

echo 5 > /proc/sys/vm/laptop_mode #&#1072;&#1082;&#1090;&#1080;&#1074;&#1080;&#1088;&#1091;&#1077;&#1090; laptop_mode
echo min_power > /sys/class/scsi_host/host0/link_power_management_policy
echo min_power > /sys/class/scsi_host/host1/link_power_management_policy
echo min_power > /sys/class/scsi_host/host2/link_power_management_policy
echo min_power > /sys/class/scsi_host/host3/link_power_management_policy
echo min_power > /sys/class/scsi_host/host4/link_power_management_policy
echo min_power > /sys/class/scsi_host/host5/link_power_management_policy
echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor 
echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
echo powersave > /sys/devices/system/cpu/cpu2/cpufreq/scaling_governor 
echo powersave > /sys/devices/system/cpu/cpu3/cpufreq/scaling_governor
echo 1 > /sys/devices/system/cpu/sched_mc_power_savings
echo 10 > /sys/module/snd_hda_intel/parameters/power_save
modprobe -r uvcvideo
echo 90 > /proc/sys/vm/dirty_ratio
echo 1 > /proc/sys/vm/dirty_background_ratio
echo 60000 > /proc/sys/vm/dirty_writeback_centisecs

```
In that article was written that I should write next code in /etc/acpi/power.sh:
```

if on_ac_power; then
<when is charging>
else
<when battery>
fi

```

but for some of that things I need to have a root access. For example the first line 
```
echo 0 > /proc/sys/vm/laptop_mode
```
works only after "sudo -i" and entering password. So how I should write it in that file? 
And the same thing about first two lines(disabling video adapter and bluetooth).

---

### Post by AlanR8 on 2012-09-02
Why don't you look at Jupiter? 

Google it. Has increased my battery life!

---

### Post by kobras on 2012-09-03
Ok thank you, this programs looks nice
But this program can't switch my video adapter off, and for me interesting how its possible to write script which will work with root permission.

---

### Post by zero2xiii on 2012-09-03
> **kobras said:**
> Ok thank you, this programs looks nice
But this program can't switch my video adapter off, and for me interesting how its possible to write script which will work with root permission.

Hay,

A lot of bark for very little bite. Turning off a video adapter that is not in use, does not save THAT much power. Test it out by manually running the commands as you state above.

Anyway, what the root permissions are considered. The power monitor script should be executed with root permissions unless I am mistaking? Not sure. You can always add the commands, detach the power, and then read the files which require root privs to be written to by "cat ./path/to/file" eg:
```
cat /proc/sys/vm/laptop_mode
```

and it should return a "0" in the output.

Best of luck, but test it out. There is a lot of other things you can do as well to save a few watts. But in the long run, it is not really worth the extra 10 minutes when the whole laptop is basically disabled or downgraded.

Cherz :)

---

