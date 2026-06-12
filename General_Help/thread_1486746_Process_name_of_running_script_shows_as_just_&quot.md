---
title: "Process name of running script shows as just &quot;sh&quot;"
date: 2010-05-18
forum: General Help
---

### Post by tgeer43 on 2010-05-18
Under 9.10 I did the following:

Added a custom application launcher to the panel which executes a script with the following command.```

sh ~/Scripts/nvidia_freq.sh
```The script contains the following code.```

#!/bin/bash
while true; do
    if on_ac_power; then
        nice /usr/bin/nvidia-settings -q all > /dev/null
    fi
    sleep 25;
done
exit 0
```This keeps my nvidia card at maximum speed. (this is pretty commonly known and used). Then to let the card go back to adaptive clocking I had another panel launcher which simply killed the associated process with the following command.
```
killall nvidia_freq.sh
```and all worked as advertised. Under 10.04 it almost works except that I am unable to kill the process because its name is now listed as simply "sh" whether I use system-monitor, top, or ps to view it. And I can't "killall sh" because it is not the only process showing with that name. The only discernable difference between them is the PID # of the process, which my panel launcher icon has no way of knowing about.

Any idea why the difference in behaviour between Karmic and Lucid? And what can I do about it?

Thanks in advance,

tgeer

---

### Post by WorMzy on 2010-05-18
Remove the sh from the start of the application launcher. What the application launcher is currently doing is running sh, and passing that script as a parameter, so the running process is sh, not nvidia_freq.sh.

---

### Post by tgeer43 on 2010-05-18
Quite right you are, WorMzy - and thanks for the fast response.
Odd, though. I could swear that is the command that I'm using in Karmic (with the 'sh'). Next time I'm at my 9.10 machine (at work) I'll have to check that.

Anyway, all is well now.

Thanks again,

tgeer

---

