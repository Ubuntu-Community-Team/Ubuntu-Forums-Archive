---
title: "Help with automatic backups."
date: 2011-03-04
forum: General Help
---

### Post by ninjapirate89 on 2011-03-04
I know I need to use cron and tar but all the sites I'm using to figure out how to do what I want are really complex. All I want to do is automatically make a backup every 12 hours of all the files in /home/ninjapirate89/.mcserver and put the tar file in /home/ninjapirate89/.mcserver-backup with the date as the file name. Can someone show me what the command would look like and tell me how to put it in cron?

---

### Post by seawolf167 on 2011-03-04
This will tar to a tar.bz2 the directory /home/ninjapirate89/.mcserver to /home/ninjapirate89/mcserver-backup.tar.bz2 every 12 hours

```
00 */12 * * * root tar -cjf /home/ninjapirate89/mcserver-backup.tar.bz2 /home/ninjapirate89/.mcserver
```

---

### Post by ninjapirate89 on 2011-03-04
Thank you very very much! :D

---

### Post by ninjapirate89 on 2011-03-04
Had to make a tweak to get it to save in the right folder and I changed my mind and made it every 6 hours instead but I have two questions that I can't figure out myself.

1. Is it possible to make the resulting filename the date and/or time instead of choosing a set filename?

2. Why does it say root in this? Is it a requirement of cron?:
```
00 */6 * * * root tar -cjf /home/ninjapirate89/.mcserver-backups/mcserver-backup.tar.bz2 /home/ninjapirate89/.mcserver

```

---

### Post by seawolf167 on 2011-03-04
> **ninjapirate89 said:**
> 1. Is it possible to make the resulting filename the date and/or time instead of choosing a set filename?

Sure - say you have 

```
outputfilename.tar.gz
```

simply replace it with

```
outputfilename$(date +%m%d%y).tar.gz
```

then the output would be "outputfilename030411.tar.gz" for today's date. Of course, you can always change this to whatever you want (since you'll probably want hours/minutes as well), type

```
man date
```

for all the available options

> **ninjapirate89 said:**
> 2. Why does it say root in this? Is it a requirement of cron?:

You can run it as any user, just replace *root* with your *username*. I set it as root because the directory had the word "server" in it, so I just figured you'd need root access to be able to access it.

---

### Post by ninjapirate89 on 2011-03-04
Oh, ok thanks. This is for making backups of my minecraft server so it doesn't need to be root to run so I'll just change it to my username. Thanks again.

---

### Post by ninjapirate89 on 2011-03-05
I hate having to keep unmarking this as solved but it still isn't working right. I woke up this morning and I didn't have any backups made. I know the command for tar works fine so I guess cron isn't doing its job. This is what I get when I type 'sudo crontab -e' in a terminal.
```

# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
0 */3 * * * ninjapirate89 tar -cjf /home/ninjapirate89/.mcserver-backups/`date +%d-%m-%y_%H:%M`.tar.bz2 /home/ninjapirate89/.mcserver

```

But when I type in 'crontab -l' it says 'no crontab for ninjapirate89'. I noticed that when I save it is saving to /tmp. Is that where it should be? Maybe there is something else I should have done? I've never used cron before so any help would be appreciated.

---

### Post by rbishop on 2011-03-05
Just throwing out my $0.02 here.

Why not just create a little script to run like this.

```

#! /bin/bash

TD=$(date '+%m-%d-%y')

tar -cjf /home/ninjapirate89/.mcserver-backup/$TD.tar.bz2 /home/ningapirate89/.mcserver

```

Then just set your cron to run that script every 6 hours.  Has always been easier in my experience to edit that script, so I don't have to keep messing with Cron....

---

### Post by CharlesA on 2011-03-05
> **rbishop said:**
> 
Then just set your cron to run that script every 6 hours.  Has always been easier in my experience to edit that script, so I don't have to keep messing with Cron....

+1. That's what I've always done and it's way easier to deal with then putting a huge line of commands inside the crontab itself.

Also, running *sudo* crontab -e shows the crontab for root, running crontab -e without sudo shows the crontab for your user. :)

---

### Post by ninjapirate89 on 2011-03-05
Ok I see. I think I have it fixed now. If it works I will change it to use a separate script instead. Thanks.

---

