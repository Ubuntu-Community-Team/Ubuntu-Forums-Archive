---
title: "Pangolin (12.04) doesn't remember brightness setting"
date: 2012-09-30
forum: General Help
---

### Post by lvshankar on 2012-09-30
I like my sceen brightness set to the lowest possible. On my Dell Vostro 1510, which I've been using Ubuntu since Edgy Eft, I can't get my setting to persist. Ever. Every reboot sets it back to full.

I've Googled, came across this: [http://askubuntu.com/a/68143](http://askubuntu.com/a/68143) but still no luck. Here's my /etc/rc.local after the above solution that seems to work for everyone else

> 
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
#echo 0 > /sys/class/backlight/acpi_video0/brightness
echo 0 > /sys/class/backlight/intel_backlight/brightness
exit 0


Commenting/Un-commenting either or both of the echo lines in rc.local makes no any difference. Any help?

---

### Post by lvshankar on 2012-10-07
Bump!

---

### Post by pqwoerituytrueiwoq on 2012-10-07
seen this thread?
[http://ubuntuforums.org/showthread.php?t=2067533](http://ubuntuforums.org/showthread.php?t=2067533)

---

### Post by essex lad on 2012-10-07
> **lvshankar said:**
> I like my sceen brightness set to the lowest possible. On my Dell Vostro 1510, which I've been using Ubuntu since Edgy Eft, I can't get my setting to persist. Ever. Every reboot sets it back to full.

I've Googled, came across this: [http://askubuntu.com/a/68143](http://askubuntu.com/a/68143) but still no luck. Here's my /etc/rc.local after the above solution that seems to work for everyone else



Commenting/Un-commenting either or both of the echo lines in rc.local makes no any difference. Any help?
Try my link [http://ubuntuforums.org/showthread.php?t=2067533](http://ubuntuforums.org/showthread.php?t=2067533)

---

### Post by lvshankar on 2012-10-07
Added it to /etc/rc.local
Screen back to full brightness on restart. The command works well though...

---

### Post by pqwoerituytrueiwoq on 2012-10-07
try running it with lightdm like this
[http://ubuntuforums.org/showpost.php?p=11656736&postcount=2](http://ubuntuforums.org/showpost.php?p=11656736&postcount=2) - reference
/etc/lightdm/lightdm.conf
 the session-setup-script runs before anything starts in the user's session so if you put [FONT=Courier New]sleep 5[/FONT] for the script it will add 5 seconds to the login time
you may want to use [FONT=Courier New]greeter-setup-script[/FONT] or [FONT=Courier New]display-setup-script[/FONT]

---

### Post by lvshankar on 2012-10-07
> **pqwoerituytrueiwoq said:**
> try running it with lightdm like this
[http://ubuntuforums.org/showpost.php?p=11656736&postcount=2](http://ubuntuforums.org/showpost.php?p=11656736&postcount=2) - reference
/etc/lightdm/lightdm.conf
 the session-setup-script runs before anything starts in the user's session so if you put [FONT=Courier New]sleep 5[/FONT] for the script it will add 5 seconds to the login time
you may want to use [FONT=Courier New]greeter-setup-script[/FONT] or [FONT=Courier New]display-setup-script[/FONT]

This works well. Thanks! 

Phew! My eyes thank you!!

---

### Post by xalatar on 2012-12-12
Hey
I just exprienced the same issue on my Vostro 3550 with Ubuntu 12.04. 

I tried all solutions I've found and only this topic helped me... 
That's my autostart script (you can put this in /etc/rc.local).
```
#!/bin/bash

sleep 3
cat /sys/class/backlight/acpi_video0/brightness 2>&1  1>/home/xalatar/bright
echo 4 > /sys/class/backlight/acpi_video0/brightness
cat /sys/class/backlight/acpi_video0/brightness 1>>/home/xalatar/bright

```If you comment line with "sleep 3" you get bright file empty. It looks like /sys/class/backlight/acpi_video0/brightness doesn't exist then (but actually I don't know why there's no error output). So, are acpi_video files created and deleted every system reboot?

EDIT:
Just moved my script into rc.local and it doesn't work. You need to create your own script in /etc/init.d and run command:
```
sudo update-rc.d scipt_name defaults
```
to get it work. But again don't know why...

---

### Post by cmcanulty on 2012-12-12
this worked for me edit etc/default/grub  line as follows back up grub first
```
GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
```

---

