---
title: "Root cronjob executes python script - fails reboot"
date: 2012-05-25
forum: General Help
---

### Post by MaOs on 2012-05-25
Hi all,

I have a python script that does some file operations and reboots after this via 

```
os.system("reboot")
```

Executing the script works fine, files are written and the machine will be rebooted. So I assume that my python code is correct.

I want to execute the script at startup (I know it's a risky to execute a script that reboots at boot time but I made sure that it does not loop infinitely).

Anyway, I am doing:

```
sudo crontab -e
```

and add

```
@reboot root /usr/bin/python /home/martin/my_script.py
```

When the machine boots up, files are written correctly but no reboot happens. The script gets invoked but the reboot is omitted.

Any idea why? I'd greatly appreciate any help.

Thanks,
-martin

---

### Post by papibe on 2012-05-26
Hi MaOs.

crontab has a very limited environment. The default PATH is reduced to just:
[LIST]
[*]/usr/bin
[*]/bin
[/LIST]
Unfortunately, reboot is in /sbin so it won't be reachable in your script as it is right now. A simple solution could be to use the full path on your system call:
```
os.system("/sbin/reboot")
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by MaOs on 2012-05-29
Hi,

I was thinking about that too and changed it but with the same result.

```
@reboot root /usr/bin/python home/martin/dhcp_study.py
```

is now in my crontab and 

```
os.system("/sbin/reboot")
``` is the statement in my python code. 
When called manually via sudo python mypython.py, it works correctly. 

Just not at boot time :(

Any more ideas?

---

### Post by MaOs on 2012-05-29
Update:

cat /var/log/syslog | grep *.py
May 29 08:29:32 hostX CRON[1204]: (root) CMD (/usr/bin/python home/maos/mypython.py)

It seems that it gets invoked with root privileges. But no reboot? Any ideas? Is there another way to invoke the script at boot time? (apart from cronjob)

---

### Post by MaOs on 2012-05-29
Okay, I found a solution.

Rather than

```
sudo crontab -e
```

I add the same line in /etc/crontab

This works fine. Anyone knows the difference or can explain the behavior?

---

### Post by matt_symes on 2012-05-29
I was going to suggest using roots crontab but i see you have.

Can you post the script ?

---

