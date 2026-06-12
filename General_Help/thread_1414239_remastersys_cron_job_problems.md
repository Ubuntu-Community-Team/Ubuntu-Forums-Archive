---
title: "remastersys cron job problems"
date: 2010-02-23
forum: General Help
---

### Post by sr_guy on 2010-02-23
Running 9.10 Karmic:

When I add this command to crontab:

```

remastersys backup ubuntu910-withfreepbx-mythtv`date +%Y%d%m%T`.iso

```

I can see the job running using ps -A | grep remast

But for some reason remastersys dies and never completes the backup. I checked remastersys.log and it's empty.

If I run the command above right from the CLI and not as a cronjob it completes the backup. Any suggestsions, or if someone has a working script to run a backup with remastersys, I'd be interested in seeing it.

---

### Post by DaithiF on 2010-02-23
Hi,
if i remember correctly, the '%' character is special when it appears in a crontab line, it indicates an end of line or end of command, so this is potentially one reason.  You could put your command into a script and call the script from cron itself, or else run your command from cron as is, but with a static filename as a test (ie. drop the date part in backticks).

---

### Post by sr_guy on 2010-02-23
I don't think it's the special characters. I changed the script I made to:

```

#!/bin/bash
cd /media/16GIG_B
rm -r ubuntu*
cd /home/remastersys/remastersys
rm -r ubuntu*
remastersys backup ubuntu910mythbox.iso
cd /home/remastersys/remastersys
cp *.iso /media/16GIG_B

```


and remastersys still died after 60 sec. Running the script from /usr/bin as root. Script is writable (chmod +x)

---

### Post by joep-vd on 2010-02-24
isn't your script running again through cron, and closes because of two instances? in that case you could make an if else command in your script, testing for the activity of remastersys.

---

