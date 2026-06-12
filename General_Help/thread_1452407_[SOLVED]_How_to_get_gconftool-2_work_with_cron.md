---
title: "[SOLVED] How to get gconftool-2 work with cron"
date: 2010-04-11
forum: General Help
---

### Post by narnie on 2010-04-11
Hello,

Been trying to make a cron job work with gconftool-2 but it won't change the wallpaper because gconftool uses DBUS now as a backend and these variables aren't set from the command line. I found this thread

[http://ubuntuforums.org/showthread.php?t=952452&page=2]("http://ubuntuforums.org/showthread.php?t=952452&page=2")

This seems to set more variables than necessary. Earlier, I found this thread on the fedora forums:

[http://forums.fedoraforum.org/archive/index.php/t-83656.html]("http://forums.fedoraforum.org/archive/index.php/t-83656.html")

This seems to be a cleaner approach, thus I wanted to share in here on the Ubuntu forums.

Here is the code:

```
export_variables () {
	user=$( whoami )
	pid=$( pgrep -u $user gnome-panel )

	for dbusenv in $pid; do
		DBUS_SESSION_BUS_ADDRESS=$( grep -z DBUS_SESSION_BUS_ADDRESS /proc/$pid/environ | sed -e 's/DBUS_SESSION_BUS_ADDRESS=//' )

		data="DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS"
		eval " export $data"
	done
}

```

Just call

```
export_variables
```

Before calling the gconftool-2 command and it should work (it does for me). Now I can happly change these for my users.

The drawback with gconftool-2 working in this way and thus the limitation of this script, is that there has to be an active gnome session for that user running.

There is no way to use gconftool-2 straight from the command line without a running gnome session thus an installer can make these changes in an install script.

I will file a bug report requesting feature versions of gconftool-2 allow sudo to run gconftool-s as a user so that it may be changed in an install script. If someone knows a trick to install like this, please post here.

Yours,
Narnie

---

