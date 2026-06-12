---
title: "Auto-login and start process on tty"
date: 2009-11-29
forum: General Help
---

### Post by Rabbitbunny on 2009-11-29
So, I'd like my "server" to boot, auto login, start screen. I'd also like the power settings to stop blanking the physical monitor. This box does not have X.

I got it to auto-login by adding this line
> **/etc/rc.local]exec /bin/login -f server[/QUOTE]

Then, I tried this said:**
> # start screen
bash ~/screen-run-check.bash

[QUOTE=~/screen-run-check.bash]#!/bin/bash
#Script to make sure process is running
EXPECTED_PROCESS_COUNT="1"
PROCESS_NAME="screen"
PROCESS_COUNT=$(/usr/bin/pgrep -c $PROCESS_NAME)
if [ "$PROCESS_COUNT" != "$EXPECTED_PROCESS_COUNT" ]; then
        screen
fi
[/QUOTE]

The process starts, which is nice, but it's not on the tty that auto-login'd.

The overall concept is to start my IRC client, My IRC bot, and a bash window in screen (which happens) and have them on the physical monitor for peripheral viewing.

I've made no progress on the power settings.

Hints?

---

