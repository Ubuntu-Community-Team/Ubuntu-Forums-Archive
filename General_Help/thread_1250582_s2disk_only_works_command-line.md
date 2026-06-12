---
title: "s2disk only works command-line"
date: 2009-08-26
forum: General Help
---

### Post by lazyfirecloud on 2009-08-26
I've finally upgraded my laptop to Jaunty and hibernate does not work anymore. Under Intrepid I had to use s2both; I had changed some script to call it when I click the button and all was well.

Currently, When I click the hibernate button, it goes black for a second and goes to the unlock screen.

I can hibernate just fine by running ```
sudo s2disk
``` command-line.

I've changed /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux such that running ```
sudo /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
``` works fine, but it does not seem to be script called when I press the button.
I also tried running ```
sudo /etc/acpi/hibernate.sh
``` but it shuts down my computer (or at least it doesn't resume properly), so I'm guessing that's also not the script called when I press the button.
I'm debating whether to change the pm-hibernate but I'm very reluctant to try doing so.

So my question is: what does Jaunty call when I click hibernate in the menu? What script do I have to change so it runs s2disk?


If anyone has any ideas, I would be more than grateful.

---

### Post by balak on 2009-09-07
AFAIK, hibernate/suspend is called by 'pm-utils' which in turn uses 
'hal' and ends up calling the script /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

What did you add in this script ? Did you reboot once after you made the changes to this script?

I have been modifying this file for every ubuntu release for the last 3 years and had no trouble. In jaunty as well, I just did that.

---

### Post by lazyfirecloud on 2009-09-09
Hi:
Thanks for your answer! 

I've rebooted several times. I'm really stumped on this. 

The script looks like this:
```

$ cat /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
#!/bin/sh

/usr/sbin/s2disk

```

based on:
```

$which s2disk
/usr/sbin/s2disk

```

I just uninstalled hibernate and rebooted. I still get that black screen and an unlock screen. 

Could it be a permission issue?
```

-rwxr-xr-x 1 root root 29 2009-08-26 16:27 /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux

```
I'm assuming it would be called with root privileges by the system.
It doesn't work with non-sudo rights as it cannot allocate memory.

---

### Post by lazyfirecloud on 2009-09-09
Digging a little deeper, it seems that gnome-power-cmd would do the same thing as the GUI

```

#!/bin/sh
# Copyright (C) 2007 Richard Hughes <richard@hughsie.com>
#
# Licensed under the GNU General Public License Version 2
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

#$1 = method name
execute_dbus_method ()
{
	dbus-send --session --dest=org.freedesktop.PowerManagement		\
		  --type=method_call --print-reply --reply-timeout=2000	\
		  /org/freedesktop/PowerManagement 			\
		  org.freedesktop.PowerManagement.$1
	if [ $? -ne 0 ]; then
		echo "Failed"
	fi 
}

if [ "$1" = "suspend" ]; then
	echo "Suspending"
	execute_dbus_method "Suspend"
elif [ "$1" = "hibernate" ]; then
	echo "Hibernating"
	execute_dbus_method "Hibernate"
elif [ "$1" = "reboot" ]; then
	echo "Rebooting"
	execute_dbus_method "Reboot"
elif [ "$1" = "shutdown" ]; then
	echo "Shutting down"
	execute_dbus_method "Shutdown"
elif [ "$1" = "" ]; then
	echo "command required: suspend, shutdown, hibernate or reboot"
else
	echo "command '$1' not recognised, only suspend, shutdown, hibernate or reboot are valid"
	exit 1
fi

```

I tried running them command-line and got the following errors:
```

$ gnome-power-cmd hibernate
Hibernating
method return sender=:1.28 -> dest=:1.128 reply_serial=2
$ dbus-send --system --print-reply --dest="org.freedesktop.Hal" /org/freedesktop/Hal/devices/computer org.freedesktop.Hal.Device.SystemPowerManagement.Hibernate
method return sender=:1.0 -> dest=:1.198 reply_serial=2
   int32 127

```
When I run the gnome-power-cmd hibernate, I get the black screen with the unlock screen.

---

### Post by lazyfirecloud on 2009-09-09
One of the two following scripts I had changed used s2both. They now both use s2disk and it works. 

```

$ cat /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
#!/bin/sh

/usr/sbin/s2disk

$ cat /usr/lib/hal/scripts/hal-system-power-hibernate
#!/bin/sh

/usr/sbin/s2disk

```

---

### Post by lazyfirecloud on 2009-09-10
well.. at least some of the time. It seems to be broken again and this time I haven't changed anything. I know better than to keep tweaking once I get something work. *sigh*

---

### Post by balak on 2009-09-13
You may get more clues by observing when it works and when it is broken.

For example, it works on a fresh boot but maybe not after you resume from hibernate once or something like that. This will give you an idea if the resume is good.

Looks like something is screwed up with jaunty and s2disk. My desktop has trouble shutting down after hibernating - which worked for all these months (years!). It writes out the disk image but then does not shutdown. I have to manually power off. Resume from hibernate (using s2disk) works just fine.

---

