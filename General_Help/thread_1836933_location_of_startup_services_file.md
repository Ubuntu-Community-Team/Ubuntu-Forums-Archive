---
title: "location of startup services file"
date: 2011-08-31
forum: General Help
---

### Post by flyingsliverfin on 2011-08-31
I was just wondering where the startup applications file is located (where the actual settings are saved)

speaking of that, where would i put a file/command that i want to run on bootup/wakeup (from hibernate or suspend)

thanks

---

### Post by Toz on 2011-08-31
To execute a command on startup, add it to **/etc/rc.local** just above the **exit 0** command.

To execute a command on resume from hibernate/suspend, create an _executable_ file in the **/etc/pm/sleep.d** directory using the following skeleton:

```
#!/bin/sh

case "$1" in
        sleep|hibernate}
                #put sleep/hibernate commands here (before sleep/hibernate)
                ;;
	thaw|resume)
		#put resume/thaw commands here (after sleep/hibernate)
		;;
esac

```

---

