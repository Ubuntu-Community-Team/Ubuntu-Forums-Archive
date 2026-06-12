---
title: "Cannot edit user level crontab"
date: 2010-12-31
forum: General Help
---

### Post by joshhowen on 2010-12-31
I use an Ubuntu server (2.6.27-7-server) to host a time and expense system for my company and I wanted to set up a cron job to automatically backup the time system and save the backup files to an external harddrive that is mounted via USB. However, I've been having what I believe to be a permissions problem when trying to add the cron job to crontab.

For examples sake lets say my username is 'user'.

When I am logged in as 'user' and I run crontab -l it shows me what is currently in crontab:

user@ubuntu:~/jtime/jtime/backups$ crontab -l
1,11,21,31,41,51 * * * *  /home/user/jtime/jtime/pi/bin/wtjob # Journyx Timesheet maintenance

I want to add another line to the crontab that looks like this:

00 00 * * * /home/user/backup_timesheets.ksh # Journyx Timesheets Backup

So the first clue that something isn't working right is that when I run crontab -e it shows me an empty file rather than what it shows me when I run crontab -l. Then, if I try adding my new entry to the empty file that crontab -e shows me I get the following error:

 [ Error writing /tmp/crontab.aLq1HX/crontab: Permission denied ]

If I look at the permissions on the temp file that was created I see this:

drwx------ 2 root user 4096 2010-12-31 10:50 crontab.aLq1HX

My tmp directory is setup to be globally writable:

ls -ltr tmp

drwxrwxrwt   6 root root 12288 2010-12-31 10:51 tmp

There also is no cron.allow or cron.deny files in my /etc directory so I don't think that's the probelm...especially since I can run crontab -l with no problems. 

Anyway, any help would be greatly appreciated. I've tried searching the forums and google in general and can't seem to come up with a solution to this problem.

Thanks in advance,

Josh

---

### Post by nitro_n2o on 2010-12-31
Did you read this [https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto) 

In Ubuntu, by default, there is not cron.allow and cron.deny, all users have permissions to create cron jobs. Read the link above and if the problem persists, you can create a cron.allow file and put ur username in it, hopefully that will fix it

---

### Post by dcstar on 2010-12-31
> **joshhowen said:**
> **I use an Ubuntu server (2.6.27-7-server)** to host a time and expense system for my company and I wanted to set up a cron job to automatically backup the time system and save the backup files to an external harddrive that is mounted via USB. However, I've been having what I believe to be a permissions problem when trying to add the cron job to crontab.

For examples sake lets say my username is 'user'.

When I am logged in as '**user**' and I run crontab -l it shows me what is currently in crontab:

user@ubuntu:~/jtime/jtime/backups$ crontab -l
1,11,21,31,41,51 * * * *  /home/user/jtime/jtime/pi/bin/wtjob # Journyx Timesheet maintenance

I want to add another line to the crontab that looks like this:

00 00 * * * /home/user/backup_timesheets.ksh # Journyx Timesheets Backup

So the first clue that something isn't working right is that when I run crontab -e it shows me an empty file rather than what it shows me when I run crontab -l. Then, if I try adding my new entry to the empty file that crontab -e shows me I get the following error:

 [ Error writing /tmp/crontab.aLq1HX/crontab: Permission denied ]
.........
[LIST=1]
[*]"2.6.27-7-server" is a kernel, not a Ubuntu version. Find out what version is installed and if it is up to date with all updates.
[*]What version of crontab is being used?
[/LIST]

---

### Post by joshhowen on 2011-01-03
nitro_n2o - Yes I had read that already. That's why I was saying that cron.allow and cron.deny didn't exist. On Ubuntu the default is to allow all uses to use cron right? I did try creating cron.allow and that didn't help though.

dcstar - Forgive my lack of knowledge but how do I find out what version of crontab I have installed? I don't see an option for a version flag. 

Thanks for the help guys...

---

### Post by joshhowen on 2011-01-03
By the way...the version of Ubuntu I am running is Ubuntu 8.10

---

### Post by b0b138 on 2011-01-03
you could try deleting the crontab and starting a new one   crontab -r

---

### Post by joshhowen on 2011-01-03
I just tried that (crontab -r) with the same results. It did delete the current crontab but I still can't create a new one due to the same permissions error.

It seems to me like the root of the issue is that I can't write to the temporary files it is creating in my /tmp directory, even though the /tmp directory is globally writable. I could easily be way off on that though...

---

### Post by gmargo on 2011-01-03
The owner and group of your temp directory do not look right to me.  If you invoke "crontab -e" as a normal user (gmargo in this example), the permissions, owner, group should look like:
```

$ ls -ld /tmp/crontab.*
drwx------ 2 gmargo crontab 4096 Jan  3 08:56 /tmp/crontab.1E3N8g

```Which makes me wonder if the permissions on your **crontab(1)** executable are correct.  They should look like this:
```

$ ls -l $(which crontab)
-rwxr-sr-x 1 root crontab 35896 Aug 24 13:45 /usr/bin/crontab

```The above info is from 10.10 Maverick, but I verified on an old 8.10 Intrepid VM that the permissions, owner, group are the same.
Note carefully that the executable is set-gid and not set-uid.

---

### Post by joshhowen on 2011-01-03
gmargo - The could easily be the problem if that's what the crontab executable permissions need to look like. Currently, they look like this:


```

ls -l $(which crontab)
-rwsr-xr-x 1 root crontab 31632 2009-05-12 17:46 /usr/bin/crontab

```

---

### Post by joshhowen on 2011-01-03
Should I change them to match what you have listed?

---

### Post by joshhowen on 2011-01-03
That looks like the right track. So now I can write to the temporary file but the changes don't get migrated to the /var/spool/cron directory. I assume because of similar permissions issues. Can you please list what the permissions should be for /var/spool/cron and /var/spool/cron/crontab?

```

/tmp/crontab.KiCt3R$ crontab -e
no crontab for user - using an empty one
crontab: installing new crontab
/var/spool/cron/crontabs/tmp.rhgpX8: Permission denied
crontab: edits left in /tmp/crontab.QvvaS3/crontab


```

Thanks

---

### Post by gmargo on 2011-01-03
```

$ ls -ld /var/spool/cron
drwxr-xr-x 5 root root 4096 Oct 22 18:35 /var/spool/cron

$ ls -l /var/spool/cron
total 12
drwxrwx--T 2 daemon daemon  4096 Nov 29 10:28 atjobs
drwxrwx--T 2 daemon daemon  4096 Nov 29 10:28 atspool
drwx-wx--T 2 root   crontab 4096 Aug 24 13:45 crontabs

$ sudo ls -l /var/spool/cron/crontabs
total 4
-rw------- 1 gmargo crontab 1103 Jan  3 09:57 gmargo

```

---

### Post by joshhowen on 2011-01-03
Well that was definitely the first part of the problem. I wonder why my permissions where all so wrong? This is the first time I've touched crontab since I installed this OS.

Anyway, I can see in the syslog that it is actually attempting to run my script now although it doesn't actually seem to be doing anything:

```

Jan  3 13:43:01 ubuntu /usr/sbin/cron[4502]: (tryon) RELOAD (crontabs/tryon)
Jan  3 13:43:01 ubuntu /USR/SBIN/CRON[15083]: (tryon) CMD (tryon /home/tryon/backup_timesheets.ksh # Journyx Timesheets Backup > /tmp/cron_josh.log)
Jan  3 13:43:01 ubuntu /USR/SBIN/CRON[15077]: (tryon) MAIL (mailed 26 bytes of output but got status 0x0004 )

```

---

### Post by gmargo on 2011-01-03
Make sure you have an MTA installed, since cron will email you any output (including stderr) from the command.

---

### Post by joshhowen on 2011-01-03
Looks like I needed to add 

```

. $HOME/.profile 

```

to the CRON job so that it can run with the right env setup. I had . /home/tryon/.profile in the script itself but that apparently didn't do it. Either way it seems to have been permissions issues the whole time.

Thanks so much for you help. It appears to be working properly now.

---

### Post by mora978 on 2011-01-05
hi joshhowen
i have the same problem. the weird thing is that i have two almost identical debian lenny systems, and on one of them the crontab works with the right permissions in the /tmp folder, on the other it doesn't. On the secon machine i always have to make writeable the crontab directory for myself to make crontab work.
Where did you add exactly the code above?

---

### Post by joshhowen on 2011-01-07
I added that little source script in the actual crontab entry that I was using. So now my crontab looks like this:

00 04 * * * . $HOME/.profile; /home/user/backup_timesheets.ksh

---

### Post by mora978 on 2011-01-07
I see, thank you!

---

### Post by krolloc1 on 2012-05-01
I know this is kind of old but the problem for me was that I had a local account named esanchez. I then joined a domain where my domain user name was the same as my local account. Even though I deleted my local account and was logging in with my domain account, I still had a crontab in /var/spool/cron/crontabs called esanchez. It had the permissions of my old local account.

I had to enable the root user and delete that crontab then disable the root user.

All worked well then.

I hope this helps some folks.

---

