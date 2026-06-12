---
title: "execute cron jobs from the command line?"
date: 2012-09-11
forum: General Help
---

### Post by sohlinux on 2012-09-11
How can I execute cron jobs from the command line?

I want to process all cron jobs in one swoop instead of waiting until the day and time they will execute.

---

### Post by spjackson on 2012-09-11
1. Put the commands you want to execute in a file.
2. Execute the file.

---

### Post by sohlinux on 2012-09-11
> **spjackson said:**
> 1. Put the commands you want to execute in a file.
2. Execute the file.

what commands do I put in a file?

fyi, im running webmin in ubuntu

---

### Post by sanderj on 2012-09-11
> **sohlinux said:**
> How can I execute cron jobs from the command line?

I want to process all cron jobs in one swoop instead of waiting until the day and time they will execute.

```
crontab -l | grep -vi -e "^#"  | awk '{$1=$2=$3=$4=$5=""}1' |  /bin/sh

```

Explanation:
[LIST=1]
[*]list crontab entries
[*]remove comment lines
[*]on the remaining lines, remove first 5 entries (=date/time stuff)
[*]then let /bin/sh run those commands
[/LIST]

Probably safe to first run:

```
crontab -l | grep -vi -e "^#"  | awk '{$1=$2=$3=$4=$5=""}1' 

```

and to check the output ...
HTH

---

### Post by spjackson on 2012-09-11
From a command prompt
```
crontab -l
```lists the commands, and more stuff besides which would need to be removed.

I've never used webmin, so I don't know how you do what you want with that I'm afraid.

---

### Post by sohlinux on 2012-09-11
> **sanderj said:**
> ```
crontab -l | grep -vi -e "^#"  | awk '{$1=$2=$3=$4=$5=""}1' |  /bin/sh

```

Explanation:
[LIST=1]
[*]list crontab entries
[*]remove comment lines
[*]on the remaining lines, remove first 5 entries (=date/time stuff)
[*]then let /bin/sh run those commands
[/LIST]

Probably safe to first run:

```
crontab -l | grep -vi -e "^#"  | awk '{$1=$2=$3=$4=$5=""}1' 

```

and to check the output ...
HTH

thanks but it appears to only execute the first cron job, not all of them?

---

### Post by sohlinux on 2012-09-11
root@server [~]# crontab -l | grep -vi -e "^#"  | awk '{$1=$2=$3=$4=$5=""}1'

output generated

     mail -s "bash history" [email]123@mail.com[/email]
     mail -s "exim_mainlog" [email]123@mail.com[/email]
     mail -s "var log messages" [email]123@mail.com[/email]


the output should be

tail -50 /root/bash_history | mail -s "bash history" [email]123@mail.com[/email]
tail -50 /var/log/exim_mainlog | mail -s "exim_mainlog" [email]123@mail.com[/email]
tail -50 /var/log/messages | mail -s "var log messages" [email]123@mail.com[/email]
     
looks like the command is missing everything before the pipe

thanks

---

