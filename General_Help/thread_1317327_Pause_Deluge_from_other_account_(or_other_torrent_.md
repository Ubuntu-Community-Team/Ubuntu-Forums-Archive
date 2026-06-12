---
title: "Pause Deluge from other account (or other torrent application)"
date: 2009-11-06
forum: General Help
---

### Post by alanwalterthomas on 2009-11-06
I download a lot of torrents. This causes problems because others want to browse the internet from their own accounts & it slows to a crawl for them.
Deluge is my favourite, but if there's only a solution for transmission or even ctorrent, that's fine.
Someday I'll get a better router that can have tomato installed, but that's someday.
I want other users to be able to double click an icon that will pause deluge in my account (or if absolutely necessary kill it)
How? Thanks,

---

### Post by alanwalterthomas on 2009-11-15
bump

---

### Post by alanwalterthomas on 2009-12-16
bump!

---

### Post by spoon_ on 2009-12-16
Pausing is hard because you have to interface with Deluge somehow. But killing is easy. Maybe someone knows how to pause it, but you can run this script in the background (on the account that's running Deluge), and it will kill deluge when a certain file is created:

```
#!/bin/sh

DIE_FILE=/tmp/deluge_die
SLEEP_TIME=1

proc=`ps -ef | grep -v grep | grep -c "sh $0"`
if [ "$proc" -gt 2 ]; then
    echo "Already running."
    exit 1
fi

while true; do
    if [ -e $DIE_FILE ]; then
        age=`stat -c %Y $DIE_FILE`
        now=`date +%s`
        if [ $(($now - age)) -lt $((2 * $SLEEP_TIME)) ]; then
            killall deluge
            echo "Killed deluge."
        fi
        rm $DIE_FILE
    fi
    sleep $SLEEP_TIME
done
```

The user that wants to kill Deluge can then run this script:

```
#!/bin/sh

DIE_FILE=/tmp/deluge_die

touch $DIE_FILE
```

Of course you can create launchers for these on your desktop so they don't appear as scripts, just icons to click on.

---

