---
title: "Upstart job not running"
date: 2012-06-13
forum: General Help
---

### Post by taylorkh on 2012-06-13
Ubuntu 12.04 32 bit

This thread is a spawn from another one dealing with a power management/wireless network issue. The other issue is at least worked around but I have come across this more generic issue. I created a simple job which I want to start with upstart. However, I have been unable to get it to run.  Here is my latest upstart file /etc/init/wifi_power_off.conf ```
# shut off power management on the wireless connection
# note that the thing is called eth1 not wlan0 as would be expected

start on started network-services

exec /sbin/iwconfig eth1 power off
exec touch /home/ken/hello_from_upstart

```Please disregard if the iwconfig command works or not. That is another matter of conjecture. I added the **touch** command so I would see that the job is executing. I do not see the file being created and thus I conclude that the job did not run.  Networking is in fact running and I can connect to the PC in question. I have also tried ```
start on RUNLEVEL=[2]
```but that does not seem to work either.

The conf file is owned by root and is not marked executable - same as other jobs in /etc/init. I would like to get a handle on setting up an upstart job. I will sort out the wireless issue later. Can anyone provide some insight? I have been studying the Upstart Cookbook and it looks like my simple example should run.

TIA,

Ken

---

