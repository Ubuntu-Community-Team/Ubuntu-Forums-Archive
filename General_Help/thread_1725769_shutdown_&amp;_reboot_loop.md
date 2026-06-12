---
title: "shutdown &amp; reboot loop"
date: 2011-04-10
forum: General Help
---

### Post by wpshooter on 2011-04-10
I have something I want to test.

How would I go about having the Ubuntu O/S shutdown after 5 minutes of run time and then automatically reboot in an endless loop until I stopped it ?  

How can I do this without having to use SUDO and have to enter password each and every time ?

Can a command for this be placed in startup applications to cause this to happen and if so, what is the exact command ?

Thanks.

---

### Post by ~Plue on 2011-04-10
i'm not an expert in bash scripting (or any for that matter), but heres an idea..

make  a script > make it executable> add to startup applications;
[I]#!/bin/bash
**#**[s]sleep 300 & - edited [/s][/I]
* sudo shutdown -r now*
[URL="https://help.ubuntu.com/community/Sudoers#Shutting%20Down%20From%20The%20Console%20Without%20A%20Password"]
modify the sudoers to not require a password for /sbin/shutdown,[/URL]
then make keyboard shortcuts to toggle the executable bit of the above script.

edit// that wouldn't interrupt the reboot at all since its already executed once you login. so when adding the command to startup applications, entering *sleep 300 && /path/to/script *might help. 

edit2//or editing rc.local as yetiman64 suggested would be even better[URL="http://ubuntuforums.org/member.php?u=1043255"]
[/URL]

---

### Post by yetiman64 on 2011-04-10
~Plue has the right commands but for your purposes they can be put in one line in the file /etc/rc.local, like,

```
sleep 300 && shutdown -r now &
``` the double ampersand sign means "then execute" and the single on the end sends the process to the background and lets rc.local finish.

The file /etc/rc.local is run on each startup as root so sudo is not required. Just leave the line > exit 0 as the last line of the file with your command put a couple of lines above it.

Must note this could cause trouble if you set too low a timeout period and the use of a recovery panel and text based editor may be necessary to fix any problems. So I would suggest you have "nano" installed if varying the sleep value lower.

---

