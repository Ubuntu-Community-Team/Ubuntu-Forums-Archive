---
title: "Resorce Monitor on Ubuntu Sever"
date: 2009-07-20
forum: General Help
---

### Post by lorderico on 2009-07-20
Is there a resource monitor for the command line Ubuntu Server 8.04?  Preferably one that I can give a command to and either get the resources being used right now, or the peak resources used in the last X days, or the average resource usage.  By resource usage I mean hard drive usage, memory usage, cpu usage, and network usage.

Thanks,

Eric

---

### Post by wojox on 2009-07-20
```
sudo top
```

---

### Post by GoldenSun on 2009-07-20
try htop
```
sudo aptitude intsll htop
```

```
htop
```

also look up some conky scripts if you want real time on your desktop.

---

### Post by prshah on 2009-07-20
> **lorderico said:**
> Is there a resource monitor for the command line Ubuntu Server 8.04?  Preferably one that I can give a command to and either get the resources being used right now, or the peak resources used in the last X days, or the average resource usage.  By resource usage I mean hard drive usage, memory usage, cpu usage, and network usage.


I don't know of any such program (not to say that there isn't one), but I suggest you create a script as follows:```

#! /bin/bash
# check for HDD problems; ie, DRDY errors
if [ `dmesg | grep -i -c drdy` -gt 0 ];
then
        touch /forcefsck
        logger "hdd_check: HDD check required, please restart system"
else
        logger "hdd_check: OK"
fi
# check current cpu usage
top -b -n 1|head -3
# check memory usage
free -lm
# check disk usage
df -h | head -1 && df -h | grep sda
# check network performance stats
netstat -s

```

Save this script (for example, as filename "srvstat") in any suitable directory in the path, and make it executable.

Then at any point ```
srvstat|less
``` will give you a one-off reading of the current server status.

If you attach the script to a cron job, you can set it to run every 30mins (or whatever interval you feel suitable) and then redirect the output to a log file of your choice (or use "logger"), then review it as and when you want.

---

### Post by lorderico on 2009-07-20
Thanks for the responses.  I like the gui and ease of use of htop.  I also like the script you provided because I can store it in a file.  However, netstat -s gives me a lot of information that I don't really need.  Is there a way to the current, average, and peak network usage including Mb usage?

Thanks,

Eric

---

### Post by lorderico on 2009-07-20
I found a better way to monitor recourses.  I installed snmp and now my network admin can monitor them remotely.

Eric

---

