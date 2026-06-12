---
title: "Crontab problems."
date: 2011-08-04
forum: General Help
---

### Post by false_chicken on 2011-08-04
I have been trying to setup a cron job to backup my Minecraft server data but I keep hitting a wall. I have a script with the following:

```
kbackup --autobg /home/will/Documents/mine.kbp
```I am trying to use Kbackup to do the job. And the task runs fine if I run it manually. The script runs too. But when cron tried to run it I get this in the syslog:

```
Aug  4 18:35:01 FALSE-PC CRON[4954]: (will) CMD (bash Scripts/bukkit_backup.sh)
Aug  4 18:35:01 FALSE-PC CRON[4953]: (CRON) error (grandchild #4954 failed with exit status 255)
Aug  4 18:35:01 FALSE-PC CRON[4953]: (CRON) info (No MTA installed, discarding output)

```The cron entry:

```
35 */1 * * * bash Scripts/bukkit_backup.sh

```

I get the same error if I try to run the command directly from cron without the script.

Any suggestions?

---

### Post by thefasterblueone on 2011-08-04
Define the full path to 'bukkit_backup.sh'.
example:  my/path/to/bukkit_backup.sh

and add this   >/dev/null 2>&1   to the end of your script so cron will stop trying to send you the error messages to your mailbox.

example:  35 */1 * * * my/path/to/bukkit_backup.sh >/dev/null 2>&1

---

### Post by bodhi.zazen on 2011-08-04
> **thefasterblueone said:**
> Define the full path to 'bukkit_backup.sh'.
example:  my/path/to/bukkit_backup.sh

and add this   >/dev/null 2>&1   to the end of your script so cron will stop trying to send you the error messages to your mailbox.

example:  35 */1 * * * my/path/to/bukkit_backup.sh >/dev/null 2>&1

chron tasks run with a minimal shell and minimal environmental variables , such as $PATH

So in scripts and in commands in cron, use the full path to binaries, directories, and files.

---

