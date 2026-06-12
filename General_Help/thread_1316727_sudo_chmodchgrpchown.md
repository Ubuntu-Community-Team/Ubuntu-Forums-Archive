---
title: "sudo chmod/chgrp/chown"
date: 2009-11-06
forum: General Help
---

### Post by kalug on 2009-11-06
Hi all,

I'd like to change **/sys/class/rtc/rtc0/wakealarm** every time I reboot my notebook, so that I don't have to answer to the passwd-promt (because normaly you have to be root to do something like this):
```
bash -c "echo 0 > /sys/class/rtc/rtc0/wakealarm"
```First I thought I could manage it by:
```
sudo chmod o+w /sys/class/rtc/rtc0/wakealarm
```or I could just change the ownership/group:
```
sudo chgrp gergito /sys/class/rtc/rtc0/wakealarm
sudo chown gergito /sys/class/rtc/rtc0/wakealarm
```But the thing is, that every time I reboot the preveleges and ownership status are set back to root according to
```
ls -l /sys/class/rtc/rtc0/wakealarm
```I don't want to login as root, nor do I want to set in visudo 
```
%gergito ALL = NOPASSWD: /bin/su
```Practically it would be the same as login' in as root...

Can please someone help me? 

Cheers Gergito

---

### Post by JillSwift on 2009-11-06
If I'm understanding what you're looking for, just put the command into /etc/rc.local

That script runs at the end of the boot cycle, and runs as root.

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR=Red]# ==========
echo 0 > /sys/class/rtc/rtc0/wakealarm[/COLOR]

exit 0
```

---

### Post by kalug on 2009-11-06
Thank you JillSwift! It works just perfect!

Have a nice weekend,

Gergito

---

