---
title: "monit with a pid, but without the process"
date: 2010-03-09
forum: General Help
---

### Post by marbour on 2010-03-09
Hi.

I need help figuring this out.

I have a process that runs without creating a PID. I know how to use pidof... So I use it to create a pidfile containing the process number.

The thing is that monit checks that the file exist... That works fine... But when I kill the process manually... leaving the pidfile, monit doesn't see this... And the process doesn't restart.

The process is flashplayer... running an swf in full screen.

Anyone has an idea?

Regards

Marc

---

### Post by marbour on 2010-03-09
Or maybe someone wants to help me with this...

My script check just fine if flashplayer is running... and restarts it if not...

The only problem when I want to cron it is... It doesn't work...

Here is the script:
```

#!/bin/sh

if ps ax | grep -v 'grep' | grep -v 'check_flashplayer' | grep 'flashplayer';
then
    echo "flashplayer running, everything is fine"
else
    screen -d -m /home/administrateur/Documents/flashplayer /home/administrateur
/Documents/starter.swf
fi

```I am totallin spaced out here... Have spent at least 20 hours searching and testing here and there...

I don't have a PIDFILE (so monit as is is out of the question - see above post) and when I can script a bash shell script that works... it doesn't when it's cron'ed...

HELP!!!

Regards

MArc

---

### Post by cjhabs on 2010-03-09
I suspect it is due to the fact that "screen" brings up a window and cron probably doesn't have any idea of the windowing environment, as it can run even when you are not logged in?

Sorry I can't be of more help than that - try redirecting stderr messages to a log file and look at what it is giving you.

---

### Post by marbour on 2010-03-09
Hi.

tried removing the screen portion of the command line without success. I am not getting this error:
> (flashplayer:5153): Gtk-WARNING **: cannot open displayGoogling a bit... I stumbled accross this: I simply had to add ```
export **DISPLAY**=:0
```in front of my code so thatmy shell script looks like this:
```

#!/bin/sh

if ps ax | grep -v 'grep' | grep -v 'check_flashplayer' | grep 'flashplayer';
then
    echo "flashplayer running, everything is fine"
else
    export **DISPLAY**=:0
    /home/administrateur/Documents/flashplayer /home/administrateur /Documents/starter.swf
fi

```All if fin now...

Thanks...

Marc

---

