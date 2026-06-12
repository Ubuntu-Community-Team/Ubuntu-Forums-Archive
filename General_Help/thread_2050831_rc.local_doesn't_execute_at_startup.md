---
title: "rc.local doesn't execute at startup"
date: 2012-08-31
forum: General Help
---

### Post by HasanOzbey on 2012-08-31
When i do: ***sudo sh /etc/rc.local*** it works perfect but when i reboot my system, it wont start.

There is my **rc.local** file:
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

sudo setxkbmap tr 
exit 0
```

I've added ***>> /var/log/rc.local.log 2>&1*** to end of my command for see what's wrong and i've got this error from the log after reboot:
```
Cannot open display "default display"
```

I also tried ***sleep X*** but it didn't work too!

Any help will be greatly appreciated.

---

### Post by dcstar on 2012-09-01
> **HasanOzbey said:**
> When i do: ***sudo sh /etc/rc.local*** it works perfect but when i reboot my system, it wont start.
.........

It works perfectly. It cannot run a X command because the X server has not started when rc.local runs (and it wouldn't even know where to send the output anyway).

Put X commands in the user Startup Appliactions that run after login on the GUI.

---

### Post by NikTh on 2012-09-01
Hello , 
Of course @dcstar has right . 

I want to add an extra tip. 

rc.local **don't need a sudo**. It executes the commands as root. 

Thanks

---

### Post by HasanOzbey on 2012-09-01
> **dcstar said:**
> It works perfectly. It cannot run a X command because the X server has not started when rc.local runs (and it wouldn't even know where to send the output anyway).

Put X commands in the user Startup Appliactions that run after login on the GUI.

Thank you so much but I'm such a newbie. I'll be appreciate it if you tell me how can i put those "X commands (?)" in the Startup Applications.

> **NikTh said:**
> Hello , 
Of course @dcstar has right . 

I want to add an extra tip. 

rc.local **don't need a sudo**. It executes the commands as root. 

Thanks

Thanks for the tip!

---

### Post by HasanOzbey on 2012-09-01
Fixed.

Created a file named "keyfix" and put this command inside:
```
setxkbmap tr
```

Moved this file to /home and ran that command:
```
chmod +x /home/keyfix
```

Added this file into *Start Applications* and it worked.

---

