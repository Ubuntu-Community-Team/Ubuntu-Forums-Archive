---
title: "Script to monitor and restart a halted/failed application"
date: 2009-10-13
forum: General Help
---

### Post by floborg on 2009-10-13
I use cron to run a script that calls icecream to record some streaming audio.  The problem is that the stream is unreliable and cuts out often.  The show of interest is 5 hours long.

I would like for my script to not only start icecream, but to monitor it.  If it fails, the script should restart it with a slightly different command - just append a value to the "-name" parameter.

Any ideas on how to do this?  Thanks.

---

### Post by rippin on 2009-10-13
> **floborg said:**
> I use cron to run a script that calls icecream to record some streaming audio.  The problem is that the stream is unreliable and cuts out often.  The show of interest is 5 hours long.

I would like for my script to not only start icecream, but to monitor it.  If it fails, the script should restart it with a slightly different command - just append a value to the "-name" parameter.

Any ideas on how to do this?  Thanks.

We're clueless without reading the script.

---

### Post by floborg on 2009-10-13
> **rippin said:**
> We're clueless without reading the script.

Here's what I run:

```
#!/bin/sh

cd /home/****/Music/DM

icecream --name dm%Y%m%d --stop 310min http://wrif.com/wriflive.pls

```

So, I'd like to modify this to watch icecream for failures, and, if it fails, to restart it with a slightly different name option.  Something like "--name dm%Y%m%d_1".  It would have to keep track of it through the full 320 minutes, and perhaps restart it multiple times.

---

### Post by rippin on 2009-10-13
> **floborg said:**
> Here's what I run:

```
#!/bin/sh

cd /home/****/Music/DM

icecream --name dm%Y%m%d --stop 310min http://wrif.com/wriflive.pls

```So, I'd like to modify this to watch icecream for failures, and, if it fails, to restart it with a slightly different name option.  Something like "--name dm%Y%m%d_1".  It would have to keep track of it through the full 320 minutes, and perhaps restart it multiple times.

I think commands like **wait**, **sleep** and **test** would be good choices.

Someone else may  be able to assist with renaming a failed transfer to another name.

 But, it may be useful to look into **monit (**[http://packages.ubuntu.com/search?keywords=monit](http://packages.ubuntu.com/search?keywords=monit)).

From: [http://mmonit.com/monit/](http://mmonit.com/monit/)
**What Monit can do**

                                                          Monit can start a process if it does not run,                             restart a process if it does not respond and stop                             a process if it uses too much resources. You can                             use Monit to monitor files, directories and                             filesystems for changes, such as timestamp                             changes, checksum changes or size changes. You can                             also monitor remote hosts; Monit can ping a remote                             host and can check TCP/IP port connections and                             server protocols. Monit is controlled via an easy                             to use control file based on a free-format,                             token-oriented syntax. Monit logs to syslog or to                             its own log file and notifies you about error                             conditions and recovery status via customizable                             alert.

Examine this page to see if you can employ it : **[http://tinyurl.com/w3nhp](http://tinyurl.com/w3nhp)**

---

### Post by floborg on 2009-10-14
Well, monit looked a little complicated, and I'm not sure I could issue a slightly different command.  Anyway, I think I've got a solution:

```
#!/bin/sh

FILENAME=1
HOUR=$(date +%I)
MINUTE=$(date +%M)

cd /home/****/Music/DM

until [ $HOUR -eq 10 ] && [ $MINUTE -ge 30 ]; do

icecream --name dm%Y%m%d_$FILENAME --stop 335min http://wrif.com/wriflive.pls

sleep 5m

FILENAME=$(($FILENAME+1))
HOUR=$(date +%I)
MINUTE=$(date +%M)

done
```

It seemed to work fine during a short-timescale test.  I actually don't need to check if icecream isn't running, since the next command will only be hit if the process ends.

---

