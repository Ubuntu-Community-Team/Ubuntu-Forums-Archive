---
title: "Crontab command substitution problem"
date: 2009-12-08
forum: General Help
---

### Post by royalibrahim on 2009-12-08
Hi all,

I am using Ubuntu 8.04 ubuntu. I have a cron job entry to run a shell script at a scheduled time. This script has a X application to be launched. As cron does not pick already exported environment variables and it runs in a separate environment, I need to export the DISPLAY variable to run my GUI process. So I am setting the DISPLAY environment variable through command substitution at the top of my script as follows: 

> export DISPLAY="`who am i | cut -d"(" -f2 | cut -d")" -f1`"It seems, this does not work with cron (i.e) cron is not executing command substitution inside shell script or at the crontab's "command field" entry:

**crontab -l** output:
> SHELL=/bin/bash

01 17 * * * export DISPLAY="`who am i | cut -d"(" -f2 | cut -d")" -f1`" && gui_process.sh &> error.log I have no other option other than hardcoding the (literal) value instead of command substitution as follows:

> #!/bin/bash

export DISPLAY="xx.xx.xx.xx:0.0"
xterm +hold -e "GUI" My questions are: 

a) Why cron does not support "command substitution"?

b) Also, I have exported DISPLAY in my .bashrc file (since my login shell is bash) and I have specified this shell at the top of the crontab as: SHELL=/bin/bash. Still why cron is not reading it from ~/.bashrc while executing my script??

c) Since cron is not associated to any terminal (/dev/tty) I guess no need for trapping HUP signal?

Thank you

---

### Post by bchurchill on 2009-12-08
cron runs scripts using sh, as opposed to bash.  sh doesn't source .bashrc, which is why that doesn't help you at all.  This is the same reason that you loose your environment variables.  As far as I know, sh fully supports setting variables the way that you've been doing.

I suspect you need to put your export command in a separate script, along with the command to start the gui process.  Try to see if your script works well in sh.  Also make sure you're script is actually running when you think it is (check cron's logs).

Another thing you could try is putting #!/bin/bash at the top of your script.  Then cron will execute it using bash, and I think .bashrc would be sourced in that case (but I'm not sure).  That way you wouldn't even have to export the DISPLAY variable.

---

### Post by bchurchill on 2009-12-08
I should have read your original post more carefully... it seems you've tried most of these things.  Your guess is as good as mine.

---

