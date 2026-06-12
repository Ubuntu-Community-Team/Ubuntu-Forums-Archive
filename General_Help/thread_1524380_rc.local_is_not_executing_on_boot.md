---
title: "rc.local is not executing on boot"
date: 2010-07-05
forum: General Help
---

### Post by bvraghav on 2010-07-05
using ubuntu-10.04/gnome

i have my printer and localhost startup written in rc.local
but it does not execute on boot/reboot

that is the report i could make (yet learning about how to use linux)
```
[COLOR=RoyalBlue]r@r-desktop:~$[/COLOR] [COLOR=Blue]ls /etc/rc.local -l[/COLOR]
-rwxr-xr-x 1 root root 540 2010-07-05 14:26 /etc/rc.local
[COLOR=RoyalBlue]r@r-desktop:~$[/COLOR] [COLOR=Blue]cat /etc/rc.local[/COLOR]
[COLOR=DimGray]#!/bin/sh -e
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
# By default this script does nothing.[/COLOR]

echo $(date) - Running >> /var/log-rc-local.log

echo Running ccpd >> /var/log-rc-local.log
/etc/init.d/ccpd start >> /var/log-rc-local.log

echo Running lampp >> /var/log-rc-local.log
/opt/lampp/lampp start >> /var/log-rc-local.log

exit 0
[COLOR=RoyalBlue]r@r-desktop:~$[/COLOR] [COLOR=Blue]cat /var/local-rc-local.log[/COLOR]
[COLOR=DarkRed]cat: /var/local-rc-local.log: No such file or directory[/COLOR]
[COLOR=RoyalBlue]r@r-desktop:~$[/COLOR] 


```**history:**
it was working for till now and suddenly gave away... looks quite strange to me... 

what is the fix?

---

### Post by mikewhatever on 2010-07-05
Try removing the three first and last lines, they seem to have been placed there by some accidental copy/paste.

---

### Post by hanlin on 2010-07-05
Try changing to #!/bin/bash

---

### Post by bodhi.zazen on 2010-07-05
The main problem with rc.local is "concurrency" , it often runs too soon (in an effort to speed up boot times).

Try adding a sleep at the top of the script 

sleep 10

You may be able to reduce the sleep time to between 3-8 seconds.

---

### Post by bvraghav on 2010-07-05
> **bodhi.zazen said:**
> The main problem with rc.local is "concurrency" , it often runs too soon (in an effort to speed up boot times).

Try adding a sleep at the top of the script 

sleep 10

You may be able to reduce the sleep time to between 3-8 seconds.

quite much seems the concurrency was the issue... 
i was successful after i used sleep 10... and was able to squeeze it to sleep 3... and dint try to squeez further...

thanks...

[COLOR=RoyalBlue][B]is there any other file that is executed/triggered after the appropriate event... so that i can place the two scripts there  instead of using a workaround like this? :-k
[/B][/COLOR]

---

