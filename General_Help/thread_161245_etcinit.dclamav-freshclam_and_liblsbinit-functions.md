---
title: "/etc/init.d/clamav-freshclam and /lib/lsb/init-functions problems"
date: 2006-04-16
forum: General Help
---

### Post by jchau on 2006-04-16
I installed clamav a while ago with freshclam.  Whenever I start or shutdown my computer, I get an error message from the /etc/init.d/clamav-freshclam script like:
> /etc/rc2.d/S20clamav-freshclam: line 151: log_daemon_msg: command not found

I think that /lib/lsb/init-functions is supposed to provide the function, but it is not in /lib/lsb/init-functions. 

Attached are copies of my /lib/lsb/init-functions and /etc/init.d/clamav-freshclam files (I had to add the .txt to attach it).

Is there a more extensive (but standard) version of init-functions I can use or should I just tell clamav-freshclam to use other functions?

---

### Post by dcstar on 2006-04-16
[QUOTE=jchau]I installed clamav a while ago with freshclam.  Whenever I start or shutdown my computer, I get an error message from the /etc/init.d/clamav-freshclam script like:


I think that /lib/lsb/init-functions is supposed to provide the function, but it is not in /lib/lsb/init-functions. 

Attached are copies of my /lib/lsb/init-functions and /etc/init.d/clamav-freshclam files (I had to add the .txt to attach it).

Is there a more extensive (but standard) version of init-functions I can use or should I just tell clamav-freshclam to use other functions?[/QUOTE]
It is a know issue with the LSB version in Ubuntu being out of date, just paste the following code on the end of your init-functions file and it will work:
```
# Sample usage:
# log_daemon_msg "Starting GNOME Login Manager" "gdm"
#
# On Debian, would output "Starting GNOME Login Manager: gdm"
# On Ubuntu, would output " * Starting GNOME Login Manager..."
#
# If the second argument is omitted, logging suitable for use with
# log_progress_msg() is used:
#
# log_daemon_msg "Starting remote filesystem services"
#
# On Debian, would output "Starting remote filesystem services:"
# On Ubuntu, would output " * Starting remote filesystem services..."

log_daemon_msg () {
    if [ -z "$1" ]; then
        return 1
    fi

    if [ -z "$2" ]; then
        echo -n "$1:"
        return
    fi
    
    echo -n "$1: $2"
}

```

---

### Post by jchau on 2006-04-16
Thanks. The init-functions file seems to have a lot of usplash stuff though. 

The clamav-freshclam also seems to call "log_progress_msg".

Is there a planned update for init-functions?

---

