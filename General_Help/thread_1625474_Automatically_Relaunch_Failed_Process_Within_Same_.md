---
title: "Automatically Relaunch Failed Process Within Same Terminal Session"
date: 2010-11-19
forum: General Help
---

### Post by zhaarteth on 2010-11-19
I'm running a game server which is still in Beta, so I am expecting it will crash while I am not there to bring it back up. The catch is, I want it to get right back into working order postmortem--from within the same terminal window.

I am neither a programmer nor directly involved in this Beta past submitting bug reports, otherwise this wouldn't even be an issue for me as I could likely just write a component (wrapper?) to the server itself to relaunch on a crash.

Now, normally I know one could just do this via cron every # minutes:
```
ps -ef|grep -v grep|grep server >/dev/null || ./server
```

However I want it to present a maximised xfce4-terminal window when it relaunches--preferably in the same one it started in.

Case-in-point: How would I go about achieving such a result? 

As a bonus I'd like to use a shiny GUI, perhaps something like gnome-scheduler for this, though not a requirement as it would only encourage my laziness. :P

---

### Post by DaithiF on 2010-11-19
I guess you could use a wrapper script to execute it continuously ... the script will block until the server command exits or crashes, and then will just run it again ... and again. ..

```
#!/bin/bash
while true
do
  ./server
done

```

---

### Post by zhaarteth on 2010-11-19
Hmmn, I'll give that a shot though I have a feeling that'd wind me up with a flood. 

Does "while true" essentially mean "while the terminal I was launched from has a prompt available" ?

EDIT: I want such a wrapper to be able to discern a manual shutdown of the server from a crash. Would something like this work for a simple timed check?

```
#!/bin/bash
# timeout.sh

#  This script checks to see if the game server is running.
#+ If not running, it waits for user input to cancel before re-runing.

while true
do

INTERVAL=5                # timeout interval

timedout_read() {
  timeout=$1
  varname=$2
  old_tty_settings=`stty -g`
  stty -icanon min 0 time ${timeout}0
  eval read $varname      # or just  read $varname
  stty "$old_tty_settings"
}

echo; echo -n "Server either exited or crashed. Enter any text to cancel restart. "
timedout_read $INTERVAL cancel

echo

if [ ! -z "$cancel" ]  # If input before timeout ...
then
  exit 0
else
  echo "No response. Relaunching server!"
  ./server
fi

echo

done
```

---

### Post by zhaarteth on 2010-11-20
This a 24th hour bump post. First of two.

---

