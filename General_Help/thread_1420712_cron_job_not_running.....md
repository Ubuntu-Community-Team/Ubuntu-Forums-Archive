---
title: "cron job not running...."
date: 2010-03-03
forum: General Help
---

### Post by switch10 on 2010-03-03
I have a cron job set up to backup my ~/ directory everyday at 10:00.  But the cron job is not running.  here is my confile that I loaded into crontab...
```
#backup everyday @ 10:00 AM and 10:30 AM
00 10 * * * /home/dave/bin/backup.sh
30 10 * * * /home/dave/bin/music_backup.sh

#move video files to server @ 11:00
00 11 * * * /home/dave/bin/backup_vids.sh

```

the *.sh are executable.  I logged out and logged back in since I put the cronfile in crontab.  The commands that I use in the *.sh files work fine when I run them manually.  

Any help?

Thanks,

Dave

---

### Post by artheus on 2010-03-03
Have you given any thoughts to using rsnapshot to do this?

When you write your crontab, how do you go on doing that? through "crontab -e" command?
Do you need to run these scripts as sudo? Have you put them in your users crontab, or super users?

//Artheus

---

### Post by switch10 on 2010-03-03
OK, this is weird.  The other 2 cron jobs work, but the one that backs up my /home dir does not??  The command is fine, when I copy and paste it into a terminal, it works great.  All of the *.sh have identical permissions.

---

### Post by switch10 on 2010-03-03
> **artheus said:**
> Have you given any thoughts to using rsnapshot to do this?

When you write your crontab, how do you go on doing that? through "crontab -e" command?
Do you need to run these scripts as sudo? Have you put them in your users crontab, or super users?

//Artheus

I do not need to use sudo.  

When I put the file in crontab, I use ```
crontab ~/bin/cronfile
``` without the -e option (what does the -e option do?  It doesn't say in the man pages).

---

### Post by 98cwitr on 2010-03-03
are you using Simple Backup or this this a manually created backup process?

---

### Post by switch10 on 2010-03-03
> **98cwitr said:**
> are you using Simple Backup or this this a manually created backup process?

It is a manually created backup with rsync.

---

### Post by artheus on 2010-03-03
> **switch10 said:**
> I do not need to use sudo.  

When I put the file in crontab, I use ```
crontab ~/bin/cronfile
``` without the -e option (what does the -e option do?  It doesn't say in the man pages).


> 
crontab -e

edit a copy of the current user's crontab file, or creates an empty file to edit if crontab does not exist. When editing is complete, the file is installed as the user's crontab file. If a user- name is given, the specified user's crontab file is edited, rather than the current user's crontab file; this may only be done by a super-user. The environment variable EDITOR determines which editor is invoked with the -e option. The default editor is ed. Note that all crontab jobs should be submitted using crontab ; you should not add jobs by just editing the crontab file because cron will not be aware of changes made this way.
[I]
quoted from [http://www.computerhope.com/unix/ucrontab.htm](http://www.computerhope.com/unix/ucrontab.htm)[/I]



Okay... Well.. could you post the scripts?

---

### Post by switch10 on 2010-03-03
this is the one that is not working as a cron job.  It works when I manually run it.

```
 rsync -vrl --progress --stats --perms --delete --exclude '*~' --exclude 'Music' --exclude 'server' --exclude 'Downloads' --exclude 'Ubuntu One' --exclude 'Videos' --exclude '.VirtualBox' /home/dave/ /media/server/backup/desktop/dave 
```

---

### Post by gmargo on 2010-03-03
> **switch10 said:**
> this is the one that is not working as a cron  job.  It works when I manually run it. ```
 rsync -vrl --progress --stats --perms --delete ..{snip}.. 
```

Is that the entire script?  Why would you use a **--progress** option in a command run from cron?  Probably **rsync(1)** is trying to open the terminal to give you a pretty progress meter and crashes because there isn't a terminal.  What errror message did it give you?

> **switch10 said:**
> (what does the -e option do?  It doesn't say in the man pages).
From the **crontab(1)** man page:
> 
       The -e option is used to edit the current crontab using the editor specified  by
       the VISUAL or EDITOR environment variables.  After you exit from the editor, the
       modified crontab will be installed automatically. If neither of the  environment
       variables is defined, then the default editor /usr/bin/editor is used.


---

### Post by switch10 on 2010-03-03
No error message.  That makes sense though taking out the --progress. I forgot to remove it. I will try again and post back if it's solved. 

Thanks.

---

### Post by DaithiF on 2010-03-03
also, as a general rule when trying to figure out why a script isn't running under cron,  first thing i do is narrow down whether  (a) a problem with the cron definition means the script isn't getting run, or (b) the script *is* being run, but its failing (silently) with an error.

a simple logging statement added as the first command in the script will do the trick 
```
echo "starting script $(date)" >> /some/path/myscript.log

```
if you get output in the logfile then you know to look at the subsequent commands in the script.  If you don't, then its a problem with the cron entry, or a failure to launch the script (lack of executable permissions, incorrect path to the script, etc)

---

### Post by switch10 on 2010-03-03
It works! :)

I removed the --progress as well as --stats.  

Thanks for the help everyone!

Dave

---

### Post by switch10 on 2010-03-03
> **DaithiF said:**
> also, as a general rule when trying to figure out why a script isn't running under cron,  first thing i do is narrow down whether  (a) a problem with the cron definition means the script isn't getting run, or (b) the script *is* being run, but its failing (silently) with an error.

a simple logging statement added as the first command in the script will do the trick 
```
echo "starting script $(date)" >> /some/path/myscript.log

```
if you get output in the logfile then you know to look at the subsequent commands in the script.  If you don't, then its a problem with the cron entry, or a failure to launch the script (lack of executable permissions, incorrect path to the script, etc)
  Thanks!  I'm going to do this as well.

---

