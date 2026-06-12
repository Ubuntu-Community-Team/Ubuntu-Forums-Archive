---
title: "ACPI WakeUp not working on PC HP Compaq dc5750"
date: 2012-04-03
forum: General Help
---

### Post by patrick31698 on 2012-04-03
[SIZE=2]Hi all,
i recently bought a second hand 
[/SIZE]**[SIZE=2]PC HP Compaq dc5750 AMD Athlon 64 X2 4400+ 2x 2.3GHz[/SIZE]**

which i want to use as a HTPC using MythTV  on a Mythbuntu install.


I installed mythbuntu 11.04 and now struggleing with the acpi wakeup.
I followed the instruction here: [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)
disabled hwclock update an hpet


Computer should be able to wake up from S4

```
patrick@WohnzimmerPC:~$ patrick@WohnzimmerPC:~$ dmesg | grep -i rtc [    0.756213] rtc_cmos 00:03: RTC can wake from S4 [    0.756255] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0 [    0.756281] rtc0: alarms up to one month, y3k, 114 bytes nvram [    0.793742] Using IPI No-Shortcut mode [    0.794158] rtc_cmos 00:03: setting system clock to 2012-03-31 23:35:38 UTC (1333236938)
```Manually testing wakealarm turns out fine (?)

```
patrick@WohnzimmerPC:~$ sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"[sudo] password for patrick:  patrick@WohnzimmerPC:~$ sudo sh -c "echo `date '+%s' -d '+ 5 minutes'` > /sys/class/rtc/rtc0/wakealarm" patrick@WohnzimmerPC:~$ cat /sys/class/rtc/rtc0/wakealarm 1333268519 patrick@WohnzimmerPC:~$ cat /proc/driver/rtc rtc_time    : 08:17:19 rtc_date    : 2012-04-01 alrm_time    : 08:21:59 alrm_date    : 2012-04-01 alarm_IRQ    : yes alrm_pending    : no 24hr        : yes periodic_IRQ    : no update_IRQ    : no HPET_emulated    : no BCD        : yes DST_enable    : no periodic_freq    : 1024 batt_status    : okay 
```But nothing happens five minutes after sudo shutdown -P now :-(

please help me with this issue.
If you need any further details let me know
Probably my problem is due to some settings in the BIOS as there is no obvious option to enable ACPI WakeUp.

---

