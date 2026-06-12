---
title: "How to STOP the computer from shutting down when e.g. making backups?"
date: 2011-11-28
forum: General Help
---

### Post by exabyte on 2011-11-28
I'm using the following script in /etc/init/delay-shutdown.conf

```

# delay-shutdown - Delay shutdown on pids in /var/run/delay-shutdown
#
# Delay shutdown on pids in /var/run/delay-shutdown

description     "Delay shutdown on pids in /var/run/delay-shutdown"

# Make sure we start before cron
start on startup and (starting cron or starting anacron)
stop on runlevel [016]

console output

pre-start script
    mkdir -p /var/run/delay-shutdown
    rm -f -- /var/run/delay-shutdown/*.lock
end script

post-stop script
    delay="yes"
    while [ -n "$delay" ]
    do
        delay=""
        for lockfile in /var/run/delay-shutdown/*.lock
        do
            if ! [ -e "$lockfile" ]
            then
                break
            fi

            pid="`cat "$lockfile" | cut -f 1 -d ' '`"
            name="`cat "$lockfile" | cut -s -f 2- -d ' '`"

            if [ -z "$name" ]
            then
                name="`ps -p $pid | tail -n 1`"
            fi

            if [ -e "/proc/$pid" ]
            then
                delay="yes"
                if [ -x /bin/plymouth ]
                then
                    /bin/plymouth message --text="$name running. Waiting for it to complete (pid $pid)" || true
                fi
                echo "$name running. Waiting for it to complete (pid $pid)"
                sleep 5
            fi
        done
    done 
end script

```

It doesn't work. It reboots immediately even though it says it's waiting in the splash screen. It works when I do "stop delay-shutdown" manually.

What's the problem?

---

