---
title: "crontabs job"
date: 2010-12-07
forum: General Help
---

### Post by kartabosh on 2010-12-07
hi, i have a problem, i don't know what exactly i'm doing wrong
i added a cron job to it and it won't work
# m h  dom mon dow   command
19 16 * * * /home/ali/.alistuff/scripts/update.sh >> /home/ali/log.log

when the time comes it does create the log file but it's empty
if i manually run that command it succeeds, the log is actually the log
so can anyone tell me what i'm doing wrong?

ali@K50AF:~$ /home/ali/.alistuff/scripts/update.sh >> /home/ali/log.log
ali@K50AF:~$

---

### Post by surfer on 2010-12-07
who has execute permissions on /home/ali/.alistuff/scripts/update.sh ? i guess cron runs as root and may not be allowed to run the script.

does
```
$ sudo /home/ali/.alistuff/scripts/update.sh >> /home/ali/log.log
```
work?

---

### Post by kartabosh on 2010-12-07
yep, it worked 
but since it's not a harmful script i guess i could chmod 777 it

update: i did it, still empty log...

---

### Post by surfer on 2010-12-07
```
 19 16 * * * **ali** /home/ali/.alistuff/scripts/update.sh >> /home/ali/log.log
```

shouldn't there be a username?

in that case only the user needs exec rights.

---

### Post by kartabosh on 2010-12-07
i'm pretty sure a username is not required since the instructions are 
# m h dom mon dow command
but let me try it anyway
nope, didn't work

---

### Post by surfer on 2010-12-07
ah, you're right, the username in required in /etc/cron.d/...

that's the variant i usually use becuase it does not interfere with system upgrades.

---

### Post by surfer on 2010-12-07
actually, no: my /etc/crontab contains entries like

```

# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly

```

what ubuntu version are you using? and are we talking about /etc/crontab or what?

---

### Post by kartabosh on 2010-12-07
i'm using ubuntu minimal 10.10 and i was "crontab -e"-ing in a terminal
it appears that if i insert it in /etc/crontab it works 
thanks :)

---

### Post by Cheesehead on 2010-12-09
To see why it's not working under your user-level crontab (crontab -e), we would need to see the script that is being triggered.

The cron environment is quite limited. Although it's your crontab, cron is running the script as cron, not you. If your script uses .bashrc aliases, environment variables, shortcuts, etc that are specific to your account then cron won't know any of those when it runs the script.

That's the most common reason cron-launched scripts fail.

---

### Post by RedScourge on 2011-05-03
I am posting this here incase someone coming here runs into the issue that I did, which took me days to figure out!

If you are using scripts named something like script.sh and they are in folders such as /etc/cron.hourly, make sure you modify your /etc/crontab (or /etc/anacrontab) file or they will not run!!!

 For example, in /etc/crontab:
  
1 * * * * root cd /tmp && run-parts --report /etc/cron.daily
  
Change to:
  
  1 * * * * root cd /tmp && run-parts --regex='(.*)' --report /etc/cron.daily


Unlike some other systems like RedHat/Fedora/etc, run-parts under Debian  or Ubuntu systems will ignore files with dots or most other characters  in their name, meaning some or all of your scripts in run-parts folders  such as /etc/cron.daily will not be run. For example  /etc/cron.daily/backup.sh will never be run with the default way that  /etc/crontab is set up.
 
 From man cron:
 
 "Files must conform to the same naming convention as used by  run-parts(8): they must consist solely of upper- and lower-case letters,  digits, underscores, and hyphens. If the -l option  is specified, then  they must conform to the LSB namespace specification, exactly as in the  --lsbsysinit option in run-parts."

---

