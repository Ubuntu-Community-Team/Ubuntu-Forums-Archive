---
title: "Can't set(edit) wakealarm"
date: 2011-05-19
forum: General Help
---

### Post by inspiral on 2011-05-19
Hi All

I'm running 11.04 with the latest packages and I didn't have this problem with the previous version.

I can't set a value in /sys/class/rtc/rtc0/wakealarm so the system will wake from suspend or poweroff.

For some reason I can't seem to edit the file /sys/class/rtc/rtc0/wakealarm anymore no matter which user I am, including root.

Anyone got any ideas ?

Thanks.


```
root@pc:/# sudo sh -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
root@pc:/# cat /sys/class/rtc/rtc0/wakealarm
root@pc:/# 

root@pc:/# sudo sh -c "echo `date '+%s' -d '+ 10 minutes'` > /sys/class/rtc/rtc0/wakealarm"
root@pc:/# cat /sys/class/rtc/rtc0/wakealarm
root@pc:/# 

root@pc:/# cat /proc/driver/rtc
rtc_time    : 15:11:58
rtc_date    : 2011-05-19
alrm_time    : 15:16:47
alrm_date    : 2011-05-19
alarm_IRQ    : no
alrm_pending    : no
24hr        : yes
periodic_IRQ    : no
update_IRQ    : no
HPET_emulated    : yes
BCD        : yes
DST_enable    : no
periodic_freq    : 1024
batt_status    : okay

root@pc:/# ls -lrt /sys/class/rtc/rtc0/wakealarm
-rw-rw-r-- 1 root root 4096 2011-05-19 15:11 /sys/class/rtc/rtc0/wakealarm

```

---

### Post by inspiral on 2011-05-22
Hi All

I'm still stuck....I've just tried re installing the ACPI packages but it hasn't made any difference.

Anyone got any ideas ?

Thanks.

---

### Post by Blonddeeni on 2011-06-07
I wish I could help but am also having exactly the same problem.
I'm hoping by "bumping" this thread someone else may notice and help.

Here's hoping.
[-o<

Blonddeeni

PS: This worked fine with my Mythbuntu-8.10, but that got messed up with the "Database schema being too new for the mythtv front/backends. So am doing a complete reinstall using 11.04.
eek!

---

### Post by inspiral on 2011-06-07
Hi

I have just managed to solve my particular issue though I'm not sure if it'll help you, hope so :)

It turns out the problem as far as I can work out was not caused by updating the OS but the move between GMT(same as UTC) and BST(British Summer) time which is GMT+1.

Prior to the time change everything worked find for me as the wake alarm commands use UTC and my local time was the same but when we moved to BST that changed.

To fix the problem I changed a setting in /etc/default/rcS so that every time the OS shuts down its writes UTC to the BIOS sys date/time.

My /etc/default/rcS now looks like this:
```

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
UTC=yes
VERBOSE=no
FSCKFIX=no
```Note this solution won't work if your system dual boots with Windows as it requires the BIOS time to be local.

Hope this helps.

---

### Post by Blonddeeni on 2011-06-08
Thanks inspiral.

I will try that when I get home on friday.

I cannot think of anything else other than maybe 11.04 needs rtc alarm to be enabled in the bios. 8.10 didn't but who knows?

Thanks again for your help.

Cheers and enjoy the summer, cold and wet down here.

B.

---

