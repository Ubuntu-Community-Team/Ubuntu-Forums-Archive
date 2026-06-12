---
title: "cron not executing command"
date: 2011-10-31
forum: General Help
---

### Post by Sharra on 2011-10-31
Hello,

I am trying to get a script my friend wrote for me to execute via cron, but for some reason it just will not work correctly.  The script is meant to check if my vpn connection is active, and if not then bring up the vpn again, since I can not maintain a stable connection to my pptp vpn in Ubuntu.  I have figured out that the problem seems to actually be related to the nmcli con up id iPredator command, when I try to have cron execute that and output the results to a file, it never executes.

The log is written every minute, but the nmcli command never brings the interface up, that exact syntax works fine when I execute it from the cli.  The log file is written every minute, but it is always empty.  Here is the actual line from my crontab:

* * * * * /usr/bin/nmcli con up id iPredator > /tmp/monitor.log

From what I can see in the system log the nmcli command is not even attempting to bring up the VPN and nothing ever shows up in the log.  I am totally stuck now, I have no idea what to review from here, anyone with more cron experience have any suggestions?

Thanks!

---

### Post by Rhizoid on 2011-10-31
> **Sharra said:**
> 

* * * * * /usr/bin/nmcli con up id iPredator > /tmp/monitor.log

Does cron pass the command line variables to nmcli as the terminal when it's activated like that?

Would ```
* * * * * "/usr/bin/nmcli con up id iPredator > /tmp/monitor.log"
``` work better?

Alternatively create a bash script to launch the command and add the script to cron.

```
#!/bin/bash

/usr/bin/nmcli con up id iPredator > /tmp/monitor.log

```

Would probably do, at it's simplest.

---

### Post by hwttdz on 2011-10-31
It's running it but it's running it in the shell that cron makes.  If you need it to launch a new gnome-terminal, you need to give cron

gnome-terminal --command="whatever you want to happen inside the terminal"

Or somesuch.

---

### Post by nzjunk on 2011-12-06
Hi, I have a similar issue and I'm at a loss.

The command is /usr/bin/nmcli con up id RVPN
I'm using the Gnome Scheduler to create my crontab. 
I run it as me (not root) so it can reference my keyring.

It works perfectly both when run manually thought the scheduler, and now that I've put it in to a bash script. It just doesn't work in crontab.

Syslog:

Dec  6 01:50:01 ***** CRON[20686]: (****) CMD (nmcli con up id RVPN # JOB_ID_4)
Dec  6 01:50:01 ***** CRON[20684]: (CRON) error (grandchild #20686 failed with exit status 4)
Dec  6 01:50:01 ***** CRON[20684]: (****) MAIL (mailed 1 byte of output; but got status 0x00ff, #012)

It's driving me wild!

---

### Post by Rhizoid on 2011-12-06
Does it work if you use cron to run the bash script instead of running the task directly?

---

### Post by nzjunk on 2011-12-10
> **Rhizoid said:**
> Does it work if you use cron to run the bash script instead of running the task directly?
It runs perfectly when transferred to the bash script and when executed through the 'run command' button in the Gnome scheduler. It just wont work in crontab...

---

