---
title: "need help with cron"
date: 2012-06-28
forum: General Help
---

### Post by supernater on 2012-06-28
I have this script in my /etc/cron.daily folder (saved as /etc/cron.daily/cleanup.sh.

#!/bin/sh
find /var/tmp/* -delete

It is supposed to delete the 10,000+ files my linux box generates everyday.  However, the /var/tmp/ folder just fills up more and more.  I can run the script manually by doing...

sudo ./cleanup.sh

The script runs fine and is executable.  What am I doing wrong?  Thanks.

Using ubuntu 10.04 and cron 3.0p|1-106ubuntu6 (from synaptic)

---

### Post by zero2xiii on 2012-06-28
Hay,

> **supernater said:**
> 
**#:/bin/sh**
find /var/tmp/* -delete


should be

```
#!/bin/sh
find /var/tmp/* -delete
```

also try altering the command to:

```
#!/bin/sh
rm -R /var/tmp/* 
exit
```

Maybe just a typo to here? Also please make sure you have set up the cron job correctly, see [here]("https://help.ubuntu.com/community/CronHowto") for more details in setting up cron jobs.

Cherz

EDIT:
Just noted something else aswell. It works when you sudo run it. Are you sure your cron job is run as root? Root access is required for editing anything in the /var/tmp/ folder.

Cherz

---

### Post by supernater on 2012-06-28
Ah, yes that was a type, it is ! in my script, not :

I use find instead or rm because I kept getting a error saying there were too many files for rm to delete.  

Yes, my cron config is run as a root.  

Is there a cron log so I can see if there are any errors?  Thanks.

Here is my crontab file....
```

# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user	command
17 *	* * *	root    cd / && run-parts --report /etc/cron.hourly
25 6	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6	* * 7	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6	1 * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#
```

---

### Post by SeijiSensei on 2012-06-28
Try removing the .sh from the end of the script's filename.  On Ubuntu and Debian the run-parts application (see /etc/crontab) ignores files with a dot in their filenames; "man run-parts" for details.  

One way to insure something runs every day is to create a symlink to the file in /etc/cron.daily/:

```

cd /etc/cron.daily
sudo ln -s /usr/local/sbin/mycronscript 

```

Notice there's no extension on mycronscript.

Crond writes entries to /var/log/syslog on Ubuntu.

---

### Post by Cheesemill on 2012-06-28
I would be more worried about why /var/tmp is filling up so quickly.

Deleting all of the files instead of figuring out why they are there is like trying to put a plaster on an amputated limb ;)

---

### Post by kjohri on 2012-06-29
I suggest the change of script name from cleanup.sh to cleanupsh. That is, remove the dot from the file name. And check the anacron configuration.

[http://www.softprayog.in/tutorials/anacron]("http://www.softprayog.in/tutorials/anacron")

---

### Post by supernater on 2012-06-29
> **Cheesemill said:**
> I would be more worried about why /var/tmp is filling up so quickly.

Deleting all of the files instead of figuring out why they are there is like trying to put a plaster on an amputated limb ;)

Ah, should have mentioned that this is server (file and web).  The webserver displays graphs of user input data and the data is stored in /var/tmp so that it does not have to be reparsed if the user wants to look at the graph again.

---

### Post by supernater on 2012-06-29
> **SeijiSensei said:**
> Try removing the .sh from the end of the script's filename.  On Ubuntu and Debian the run-parts application (see /etc/crontab) ignores files with a dot in their filenames; "man run-parts" for details.

> **kjohri said:**
> I suggest the change of script name from cleanup.sh to cleanupsh. That is, remove the dot from the file name. And check the anacron configuration.

[http://www.softprayog.in/tutorials/anacron]("http://www.softprayog.in/tutorials/anacron")

Ah, that might be it!  I'll run it as soon as I get home

EDIT:

This did not work for me.  I'm starting to wonder if my crontab file is misconfigured.

---

### Post by erind on 2012-06-29
> **supernater said:**
> I have this script in my /etc/cron.daily folder (saved as /etc/cron.daily/cleanup.sh.

#!/bin/sh
find /var/tmp/* -delete

It is supposed to delete the 10,000+ files my linux box generates everyday.  However, the /var/tmp/ folder just fills up more and more...

[...]

Just a thought. Given that you're dealing with 10000's of files you **might **be hitting "*Argument list too long*" error and cron does not report it, unless you redirect the error stream to some output file.
I did some testing with 200,000 files and I got:

```
$ find test_dir/* -ls
**bash: /usr/bin/find: Argument list too long**
```To avoid that error, remove the star from the find's path, so it looks like:

```
find /var/tmp/ -delete
```Also as previously said you should find out why /var/tmp is filling up in the first place.

---

