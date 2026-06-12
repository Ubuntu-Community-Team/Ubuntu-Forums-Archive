---
title: "Modem-manager (NetworkManager) fills up logs"
date: 2010-11-23
forum: General Help
---

### Post by Zwiebi on 2010-11-23
I was curious about the constantly blinking HDD led on my netbook, and I  found out, that the modem-manager daemon constantly spamming my logs.
The affected logs are syslog, daemon.log and debug.

The modem-manager service drops a line every 2 second (actual time) to these 3 logfile.

It is just a conncetion information, like this:

Nov 19 12:11:04 zwbnoti modem-manager: Duration: 3012 Up: 0 Kbps Down: 0 Kbps Total: 6454 Total: 15560
Nov 19 12:11:06 zwbnoti modem-manager: Duration: 3014 Up: 11 Kbps Down: 3 Kbps Total: 6456 Total: 15561
Nov 19 12:11:08 zwbnoti modem-manager: Duration: 3016 Up: 0 Kbps Down: 0 Kbps Total: 6456 Total: 15561

I tried "invoke-rc.d dbus restart", but it didn't helped.

I'm  using Ubuntu 10.10 with a Huawei E1750 3G modem.

Thank you for your help!

---

### Post by ThomasNovin on 2011-01-11
There is a bug on Launchpad about it:

[https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/662791](https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/662791)

---

### Post by ThomasNovin on 2011-01-11
I created a little workaround for this problem.

To apply:

```
sudo -s
cat <<_EOF_>/etc/rsyslog.d/49-modemmanager-workaround.conf
# Workaround for bug from modemmanager spamming the logs
# https://bugs.launchpad.net/ubuntu/+source/modemmanager/+bug/662791

:msg, contains, "Duration: " ~

& ~

:msg, contains, "Access Technology: " ~

& ~
_EOF_
service rsyslog restart
```

This will prevent modemmanager writing these two types of messages to any log. Works for me at least.

---

### Post by sonnettie on 2011-01-14
first download the modem-manager 0.4 source files, then in the plugins folder
 open "mm-modem-huawei-gsm.c" 

add the following  to line 30...

[B][COLOR="DarkOrchid"]
#include "mm-options.h"
[/COLOR][/B]
 

then on line 519 change...

[B][COLOR="MediumTurquoise"]    g_debug ("Access Technology: %d", act);
[/COLOR][/B]

to...

[B][COLOR="DarkOrchid"]    if (mm_options_debug ()){
        g_debug ("Access Technology: %d", act);}[/COLOR][/B]

then on line 533 change...

[B][COLOR="MediumTurquoise"]        g_debug ("Duration: %d Up: %d Kbps Down: %d Kbps Total: %d Total: %d\n",
                 n1, n2 * 8 / 1000, n3  * 8 / 1000, n4 / 1024, n5 / 1024);[/COLOR][/B]

to...

[B][COLOR="DarkOrchid"]        if (mm_options_debug()) {
            g_debug ("Duration: %d Up: %d Kbps Down: %d Kbps Total: %d Total: %d\n",
                     n1, n2 * 8 / 1000, n3  * 8 / 1000, n4 / 1024, n5 / 1024);}[/COLOR][/B]

then using Terminal "**cd**" to the modem-manager directory (source)
ie: "//home/username/Downloads/modem-manager"

and run

[B]./configure
make
make instal[/B]l

you may need to get some dev dependences using apt-get install or synaptic or whatever u use

this way the problem will be fixed not worked around ;)
and the info will still log if in debug mode

ps the" mm_options_debug()" function is defined in "mm-options.h" file in the "src" folder if anyone was looking...

EDIT:

just thought anyone else will need to look in whatever "*.c" file in the plugins folder that corisponds to there modem vendor yours is huawei but others might not be.

---

### Post by sonnettie on 2011-01-14
dual post

---

### Post by ThomasNovin on 2011-02-27
This is fixed now so just having a updated system will resolve this issue.

---

