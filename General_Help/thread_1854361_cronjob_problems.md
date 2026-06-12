---
title: "cronjob problems"
date: 2011-10-04
forum: General Help
---

### Post by Drenriza on 2011-10-04
Hi all.

I have created a script (on mac, but i hope someone can help me) where i in my crontab have written
```
5 * * * * /path/to/script/
```
And the script starts as expected.

If i execute the script by hand ./scriptName it runs 100% as expected.
If i run the crontab job (the script) then it runs the script, but the commands get weird.

Example
```
test=$(date |awk '{print $5}'
```
the output is not the time in the format hh:mm:ss instead i get CEST as output.
I need to write the command as 
```
test=$(date |awk '{print $4}'
```
To get the time output, why is that? Even if i edit the command to
tid=$(/bin/date |/usr/bin/awk '{print $5}')
it still gives me CEST as output.

What is the difference by running a command by "hand" and by crontab?

Also as some point it runs into a if then statement.
```
if [ "$test" == "10.1.42" ]
then
	(echo "Connection to the fileserver -> Level3 folder established ${tid}" >>     /Users/$hvem/startUpScripts/log)
	/Users/$hvem/startUpScripts/Level3ExpectScript
else
	(echo "Your not on the correct network 10.1.42.* didn't mount ${tid}" >> /Users/$hvem/startUpScripts/log)
fi
```

The statement is true, but it only run the echo command and skips the expect script at
/Users/$hvem/startUpScripts/Level3ExpectScript
I cant say i understand the issue i'am having.

Is their someone who can help me in the right direction?

Thanks on advance.
Kind regards.

---

### Post by collisionystm on 2011-10-04
Ok this might be a permissions issue.

Are you invoking SUDO anywhere in your process? Do you use it when running your script or editing crontab?

---

### Post by Lars Noodén on 2011-10-04
Look in /var/log/syslog, that's where errors with cron are reported.

---

### Post by collisionystm on 2011-10-04
in your crontab, put this at the very top 

MAILTO=youremailaddress

This will email you any errors cron experiences every time it runs.

---

### Post by prodigy_ on 2011-10-04
> **Drenriza said:**
> ```
awk '{print $5}'
```
You don't want to rely on this in an unattended script unless you really have no other option. Something like ```
perl -ne 'print if s/.*(\d{2}:\d{2}:\d{2}).*/\1/'
``` will work more predictably. However, in your case even this isn't necessary because **date** allows you to choose output format. Try ```
date +%T
``` or consult **man date** for more options. Other than that you probably want to redirect mail like **collisionystm** suggested and enable trace logging in your script (assuming sh/bash it's **set -x** command) to see exactly how commands are being executed.

---

### Post by Lars Noodén on 2011-10-04
> **prodigy_ said:**
> You don't want to rely on this in an unattended script unless you really have no other option.



Instead of using a pipe and awk, the just use [date](http://linux.die.net/man/1/date) by itself.
```

/bin/date +"%Z"

```

---

### Post by Jonathan L on 2011-10-04
> **Drenriza said:**
> 

What is the difference by running a command by "hand" and by crontab?


Hi Drenriza

You'll find the main differences between running by hand (ie, in your normal interactive shell) and by crontab is that the environment is different.

You'll probably find it instructive to run a cron job
```
5 * * * * printenv > /tmp/PRINTENV.cronjob
```And also manually
```
blahblah$ printenv > /tmp/PRINTENV.shell
```And then compare the difference.  It's common for all kinds of differences to show up, because cron doesn't run any of your usual .profile or .bashrc initialisations.  I'm guessing you have a locale set in your startup scripts, which is affecting the output of date.  (What is the usual output you get?)

My PRINTENV.cronjob made as above is simply
```
HOME=/home/myusername
LOGNAME=myusername
PATH=/usr/bin:/bin
SHELL=/bin/sh
PWD=/home/myusername
```whereas the interactive one has about 40 environment variables defined.

Hope that's of some use.

Kind regards
Jonathan.

---

### Post by Drenriza on 2011-10-06
Jonatan L
> And then compare the difference. It's common for all kinds of differences to show up, because cron doesn't run any of your usual .profile or .bashrc initialisations. I'm guessing you have a locale set in your startup scripts, which is affecting the output of date. (What is the usual output you get?)

I dont as such get an output. The script is a script to map a samba share.
The script works as follows.

#by looking at the en0 or en1 (wired and wireless) ip addresses, it determines if my computer is on the corporate network
#if i'am on the corporate network and i am not already connected a connection is established.
by calling an expect script to make the connection
#f i'am on the corporate network and my share is already mapped the script is aborted.

But for some reason, the script arrives at the correct if statement (true) but it docent call the expect script. It just skips it.

---

