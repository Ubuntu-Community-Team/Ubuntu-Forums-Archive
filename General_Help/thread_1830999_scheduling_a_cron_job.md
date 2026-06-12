---
title: "scheduling a cron job"
date: 2011-08-22
forum: General Help
---

### Post by itba on 2011-08-22
hi,
If I wanted to schedule a perl script to run every weekday at 1800 hours, should I setup a cron job. once I do so, if I want to cancel it, how do I undo it.
do I have to just type this at the shell prompt to set up
```

0 18 * * 1-5 root /home/test.pl

```thx!

---

### Post by jfed on 2011-08-22
This may help.

[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by itba on 2011-08-22
thanks jfed, that was helpful :p

---

### Post by itba on 2011-08-22
well, i set it up and it did not work
I typed crontab -l at the prompt and it shows 
```


# 0 19 * * 1-5 /home/test.pl

```

how do i make it run?

---

### Post by seventyeights on 2011-08-22
Is there really a hash # at the beginning of that line in your crontab? If there is, get rid of it. It's for notations and will be ignored.

---

### Post by itba on 2011-08-22
yes indeed, seventyeights, there was, and I got rid of it. I even got rid of the leading space before the 0. hopefully it will run this time...I will update here...thx!

---

### Post by itba on 2011-08-22
well, it still did not run
I ran the following:
```

ps -ef | grep cron 

```and it returned:
```

root      1428     1  0 20:06 ?        00:00:00 cron

```
I revised my crontab now to the following
```

0 22 * * 1-5 /home/test.pl >>/home/cron.test 2>&1

```

---

### Post by seventyeights on 2011-08-22
I don't know if you can log the stderr directly from cron. (the log example in the howto is a script) Maybe you could try incorporating you perl and the stderr in a bash script and run the script from cron?

---

### Post by itba on 2011-08-22
how do I do that?

---

### Post by Cheesehead on 2011-08-22
Is the script really at /home/test.pl instead of /home/$username/test.pl ?

Do you really want to run this script as root?
(It's amazing how often the answer turns out to be 'no, I didn't realize it was')

Is this a script you want to activate/deactivate a lot?
If so, there are easy ways to script that using /etc/cron.d/

Most importantly, have you documented this script so six months later you can remember what it does, why you did it, and how to maintain it?

It's very easy to test if there is a problem with cron/crontab, and with your script: Just add a line like the following to the crontab:
* * * * * root /usr/bin/touch /tmp/touchtestfile
Every minute, cron will simply touch that tempfile. Delete it, and cron should put it back a minute later. If it does, then cron and crontab are working properly. (Don't forget to remove the line when finished)

To see script errors, check syslog for cron activity at the appropriate time. Post the errors here if you want help understanding them.

You can also put flagging actions in the script (like touching the tempfiles or logging to syslog) to debug it. Remember that cron does not use the same environment variables you do, so if you have made an assumption about a directory or a display, etc. it will break the script when cron runs.

---

### Post by dave01945 on 2011-08-22
just to make sure have you tested your sript to see if it works in terminal

---

### Post by itba on 2011-08-22
[COLOR=Navy]@dave, yes, it does work in the terminal - the reason I wanted to set it up as a cron job is because I forget to run it somedays and I don't want to miss running it.

[/COLOR] [COLOR=Navy]         @cheesehead, [/COLOR]
Is the script really at /home/test.pl instead of /home/$username/test.pl ? 

Do you really want to run this script as root?
(It's amazing how often the answer turns out to be 'no, I didn't realize it was') 

[COLOR=Navy] guess I have to say that too :-(....I just revised it to /home/ba/perl/test.pl [/COLOR]

Is this a script you want to activate/deactivate a lot? [COLOR=Navy]I don't plan to, but I would like the option to do so if I have to[/COLOR]
If so, there are easy ways to script that using /etc/cron.d/ 
[COLOR=Navy]alright, how do I do that.[/COLOR]

Most importantly, have you documented this script so six months later  you can remember what it does, why you did it, and how to maintain it? 
[COLOR=Navy]yes, very much indeed[/COLOR]

It's very easy to test if there is a problem with cron/crontab, and with  your script: Just add a line like the following to the crontab:
* * * * * root /usr/bin/touch /tmp/touchtestfile
Every minute, cron will simply touch that tempfile. Delete it, and cron  should put it back a minute later. If it does, then cron and crontab are  working properly. (Don't forget to remove the line when finished)
[COLOR=Navy]ok, so now my code looks like this[/COLOR]
```

0 23 * * 1-5 /home/ba/perl/test.pl >>/home/ba/perl/cron.test 2>&1
* * * * * root /usr/bin/touch /tmp/touchtestfile

```To see script errors, check syslog for cron activity at the appropriate  time. Post the errors here if you want help understanding them.
[COLOR=Navy]ok[/COLOR]

You can also put flagging actions in the script (like touching the  tempfiles or logging to syslog) to debug it. Remember that cron does not  use the same environment variables you do, so if you have made an  assumption about a directory or a display, etc. it will break the script  when cron runs.

---

### Post by itba on 2011-08-22
where do I check the syslog?
also, I don't see any touchtestfile in /tmp directory yet...

---

### Post by Cheesehead on 2011-08-22
Oops - if the crontab is not root, then change
```
0 23 * * 1-5 /home/ba/perl/test.pl >>/home/ba/perl/cron.test 2>&1
* * * * * root /usr/bin/touch /tmp/touchtestfile
```
 to (remove the 'root', and put the test first):```
* * * * * /usr/bin/touch /tmp/touchtestfile
0 23 * * 1-5 /home/ba/perl/test.pl >>/home/ba/perl/cron.test 2>&1

```If the test is after the script, then it won't run of the script fails and cron errors out.

----

To check the syslog:
```
cat /var/log/syslog | grep cron
```
You are interested only in the ones near the end of the list


----

To make a cronjob easy to activate/deactivate (expecially from another script):

Cron will run all crontab files in /etc/cron.d/ . It checks that directory every minute.
So you can add a crontab file to activate it, and remove the same file to deactivate it:

For example, here's a crontab file. Let's call it /home/me/project/foo-crontab:```
0 18 * * * me /bin/do /home/me/foo

```
There is no header, nothing else. Note that it's in root crontab format ('me' is the username)

It needs to have permission 644 to work.
```
sudo chmod 644 /home/me/project/foo-crontab
```

And then your scripts simply do the following (as root) to activate/deactivate it:
```
cp /home/me/project/foo-crontab /etc/cron.d/me-project-crontab  # Activate
rm /etc/cron.d/me-project-crontab  # Deactivate
```

---

### Post by dave01945 on 2011-08-22
have you tried calling perl first

```
0 23 * * 1-5 /usr/bin/perl /home/ba/perl/test.pl
```

---

### Post by itba on 2011-08-22
ok cool
I fixed the code and I see the touchtestfile now...and yes, upon deletion it gets created again
I have the job scheduled to run now...it didn't run....I had just run it manually a few minutes ago as perl test.pl and it worked fine...where do i look for the error log?

---

### Post by itba on 2011-08-22
@dave, no I didn't call perl first....let me fix that and see if it runs...will post

---

### Post by itba on 2011-08-22
brilliant, it worked....thx guys!

---

