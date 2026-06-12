---
title: "Interactive startup script"
date: 2009-11-21
forum: General Help
---

### Post by dashu on 2009-11-21
Hello everyone,

I'm trying to get an interactive script to work at startup under Kubuntu 9.10 (though I believe this is not limited to Kubuntu). The script prompts the user for a password to mount a truecrypt volume:

```

#!/bin/sh

### BEGIN INIT INFO
# Provides:          truecrypt
# Required-Start:    <interactive>
# Required-Stop:     umountfs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# X-Interactive:     true
# Short-Description: truecrypt
# Description:       truecrypt
### END INIT INFO

case "$1" in
    start)
        log_action_begin_msg "Mounting /dev/sda4"
        truecrypt -t -k "" --protect-hidden=no /dev/sda4 /home/user
        log_end_msg $?
        ;;
    stop)
        log_action_begin_msg "Unmounting /dev/sda4"
        truecrypt -t -d
        log_end_msg $?
        ;;
    *)
        echo "Usage: /etc/init.d/truecrypt {start|stop}"
        exit 1
        ;;
esac

exit 0

```I put it under /etc/init.d/truecrypt, set the appropriate rights and ran
> $ sudo update-rc.d truecryptDuring startup, I would expect to see the log message "Mounting /dev/sda4" followed by a password prompt on tty[1-6], but instead I get neither and have to log in and start the script manually...

Any ideas?

---

### Post by clayreiche on 2010-05-08
Any response to this? I need to do the same thing!

Clay

---

