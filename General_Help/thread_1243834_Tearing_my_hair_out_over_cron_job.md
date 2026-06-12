---
title: "Tearing my hair out over cron job"
date: 2009-08-18
forum: General Help
---

### Post by Mander on 2009-08-18
I am trying to figure out why this doesn't work anymore.  Before I upgraded from Hardy to Jaunty, I had a couple of scripts that created a .tar archive from a list of files and emailed it to me every day, then did the same with a slightly different list of files once a week.  I copied the scripts and the crontab file when I upgraded, and reinstalled stuff as appropriate, but it doesn't seem to work.

Here is the first script, called ThesisDailyBack (I saved it without a .sh extension):

```

#!/bin/bash
DATESTAMP=`date +%Y%m%d`
cd /home/amandav/Documents/PhD/Writing/
tar --create --gzip --file=DailyBackup.tar.gz --files-from=ThesisListDaily.txt
echo &#8220;Daily Backup $DATESTAMP.&#8221; | mutt -a DailyBackup.tar.gz -s "DailyBackup.tar.gz" xxx@googlemail.com

```

the file ThesisListDaily.txt contains a list of files that are in the /Writing/ directory:

```
AllOneFilePreamble.tex
AllOneFile.tex
currentrefs.bib
AllOneFilePreamble.dvi

```

The weekly script is the same, except that the name of the .tar file is different, the list of files is longer, and some of them are in a different directory:

```

AllOneFilePreamble.tex
AllOneFile.tex
amandamod.bst
currentrefs.bib
AllOneFilePreamble.dvi
tweaklist.sty
/media/DATA/AmandaV/Documents/PhD/Images/DrawingBuenAire1Panel2WintcherDigitrace.ps
/media/DATA/AmandaV/Documents/PhD/Images/DrawingBuenAire2_2-6Mateo.eps

```

I'm not sure if the directory change is a problem, but I haven't been able to get this to run even without it.

The crontab file looks like this:

```
30 00 * * 0 /home/amandav/Scripts/ThesisDailyBack.sh;>/dev/null 2>&1;> /home/amandav/Scripts/Daily.log
00 22 * * 0 /home/amandav/Scripts/ThesisWeeklyBack.sh;>/dev/null 2>&1;> /home/amandav/Scripts/Weekly.log
```

The idea is that it will create the archive, email it to me with a date stamp in the subject line, and write a log if something goes wrong.  The script works if I run it directly, and it used to work in Hardy.  

I've read so many how-tos and help files that I am thoroughly confused, and I don't know what is different.  Can anyone give me a pointer?

---

### Post by seventyeights on 2009-08-18
It looks like your daily backup should only work on Sundays. Change that fifth tab from 0 to *.

Also, did you simply copy and past the cron file? I haven't used cron for a while, but I remember using the command $crontab -e  to set it in the system.

---

### Post by Mander on 2009-08-20
:redface:  What a dumb mistake!  Thank you for pointing it out.  I must have changed something when I copied it.

It seems to work now.

BTW, I copied it from the text editor and pasted it into the editor you get with crontab -e (using middle click; is it nano?). 

Now I just have to figure out how to send all the files from different directories...

---

### Post by Mander on 2009-08-23
I spoke too soon.  It still doesn't run automatically.

Following some other instructions, I did the following:

```
amandav@amandav-laptop:~$ ls -la /etc/cron.hourly/crontest.sh
ls: cannot access /etc/cron.hourly/crontest.sh: No such file or directory
amandav@amandav-laptop:~$ crontab -e
crontab: installing new crontab
amandav@amandav-laptop:~$ ls -lut /etc/init.d/cron
-rwxr-xr-x 1 root root 2653 2009-07-14 11:09 /etc/init.d/cron
amandav@amandav-laptop:~$ ps -el | grep cron
5 S     0  3221     1  0  80   0 -  4993 hrtime ?        00:00:00 cron
amandav@amandav-laptop:~$ ls -lut /etc/crontab
-rw-r--r-- 1 root root 724 2009-07-14 11:09 /etc/crontab

```

Which tells me that it hasn't run automatically since July 14th, I think.  But cron seems to be started, so why isn't it doing anything?

---

### Post by Judinous on 2009-09-07
Try changing the first line in your backup script to:

```
DATESTAMP=`date +\%Y\%m\%d`
```

I was fighting over a similar problem for the past few weeks.  Apparently, cron now requires escape characters before the % symbol when using the date command, even though bash does not.

---

### Post by DaithiF on 2009-09-07
Hi,
> **Judinous said:**
> Try changing the first line in your backup script to:

```
DATESTAMP=`date +\%Y\%m\%d`
```I was fighting over a similar problem for the past few weeks.  Apparently, cron now requires escape characters before the % symbol when using the date command, even though bash does not.

not quite -- cron does indeed treat '%' as a special character, and when used in a cron entry, it must be escaped with as \% as you say.  however, that doesn't extend to a script which cron calls.  so, if your crontab contained something like:
```
5 * * * * * date +%Y%m%d >> /home/me/mycron.log
```
then you'd need to escape the '%' chars, like:
```
5 * * * * * date +\%Y\%m\%d >> /home/me/mycron.log
```
but if your crontab is:
```
5 * * * * * /home/me/somescript.sh
```
then that somescript.sh file should not require any special treatment of '%' characters.

---

### Post by hockercs on 2009-09-15
Any updates to this as I am having the same issue

---

### Post by mysoogal on 2009-09-15
maybe you need to chmod +x myscript.sh again since you reinstall system right ? 

fix that date and set BASH Script Executable Throughout Your Whole System, :confused:

if you still have problems, you better install this, go with this

[http://gnome-schedule.sourceforge.net/](http://gnome-schedule.sourceforge.net/)

its way better when you have a GUI

---

### Post by Mander on 2009-09-16
I chmod'ed all the scripts when I installed them after upgrading.  I just checked them to be sure they are exectuable.

Also, adding the \ to the date command didn't work.

The scripts still don't run.

---

### Post by DaithiF on 2009-09-16
just to recap, you have these 2 entries in your user's crontab, and neither is running ... is that right?
```
30 00 * * 0 /home/amandav/Scripts/ThesisDailyBack.sh;>/dev/null 2>&1;> /home/amandav/Scripts/Daily.log
00 22 * * 0 /home/amandav/Scripts/ThesisWeeklyBack.sh;>/dev/null 2>&1;> /home/amandav/Scripts/Weekly.log

```
so a few things:
1. try adding the simplest possible job to your crontab to make sure that your crontab is actually being executed:
```
* * * * * date >> /home/amandav/crontest.log

```2. The redirections in your 2 cron entries above look strange -- there are semi-colons (statement separators) where there shouldn't be, and you seem to be trying to redirect stdout twice.  Try this instead:
```
30 00 * * 0 /home/amandav/Scripts/ThesisDailyBack.sh > /home/amandav/daily.log 2>&1

```3. Add the line:
```
MAILTO=""

```to the top of your crontab file.  This is to workaround a subtle cron bug which causes jobs which generate a lot of output to fail silently.

good luck

---

### Post by muteXe on 2009-09-16
"Tearing my hair out over cron job" would make an excellent song title.

---

### Post by amac777 on 2009-09-16
Shouldn't you be consistent on whether the script has a .sh extension or not?

> **Mander said:**
> Here is the first script, called ThesisDailyBack (I saved it [COLOR="Red"]without a .sh extension[/COLOR]):

> 30 00 * * 0 /home/amandav/Scripts/[COLOR="Red"]ThesisDailyBack.sh[/COLOR];>/dev/null 2>&1;> /home/amandav/Scripts/Daily.log
00 22 * * 0 /home/amandav/Scripts/ThesisWeeklyBack.sh;>/dev/null 2>&1;> /home/amandav/Scripts/Weekly.log

---

### Post by jondkent on 2009-09-16
Aside from the removal of the semi-colons, you might find it better to handle the logging within the script itself, either to a separate file or via syslog using the logger utility (which is my usual method).

---

### Post by Mander on 2009-09-17
> **amac777 said:**
> Shouldn't you be consistent on whether the script has a .sh extension or not?

Sorry, that was a typo.  I've tried it both ways, and neither seem to work. I've made all of the changes described above, too, and they don't seem to work.

crontest.log was generated, however.

---

### Post by DaithiF on 2009-09-17
interesting.  could you post the contents of your crontab here again please?

---

### Post by Mander on 2009-09-17
```

MAILTO=""
USER=amandav
HOME=/home/amandav
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/amandav/bin:/media/DATA/AmandaV/Documents/Scripts
DISPLAY=:0.0
MAILTO=amandav

20 13 * * * /media/DATA/AmandaV/Documents/Scripts/ThesisDailyBack > /media/DATA/AmandaV/Documents/Scripts/Daily.log
20 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupFiles;>/dev/null 2>&1;> /media/DATA/AmandaV/Documents/Scripts/Files.log
30 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupTables;>/dev/null 2>&1;> /media/DATA/AmandaV/Documents/Scripts/Tables.log
40 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupImages;>/dev/null 2>&1;> /media/DATA/AmandaV/Documents/Scripts/Images.log
* * * * * date >> /home/amandav/crontest.log

```

---

### Post by DaithiF on 2009-09-17
Hi,
the effect of adding the MAILTO="" command at the top is negated by the fact that you have MAILTO=amandav a few lines below!  So remove the MAILTO=amandav line.  Also the 2nd, 3rd and 4th cron command entries still have the ';' characters, they should also be removed.

---

### Post by Mander on 2009-09-18
I had just left those other two for the time being, but I've changed it now.

Crontab now reads:
```

MAILTO=""
USER=amandav
HOME=/home/amandav
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/amandav/bin:/media/DATA/AmandaV/Docume$
DISPLAY=:0.0

09 01 * * * /media/DATA/AmandaV/Documents/Scripts/ThesisDailyBack > /media/DATA$
20 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupFiles > /dev/null$
30 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupTables >/dev/null$
40 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupImages >/dev/null$
* * * * * date >> /home/amandav/crontest.log
```

But it still doesn't work.

---

### Post by DaithiF on 2009-09-18
I don't know.  Time to start adding some logging statements to your script to see (a) whether its actually getting called, and (b) how far it gets if so.  So at the top of your script, add something like:
echo "started script" >> /home/amandav/script.log
and if you get some output from that, then add further echo statements after each line to see how far it gets before failing.

---

### Post by Mander on 2009-09-19
> **DaithiF said:**
> I don't know.  Time to start adding some logging statements to your script to see (a) whether its actually getting called, and (b) how far it gets if so.  So at the top of your script, add something like:
echo "started script" >> /home/amandav/script.log
and if you get some output from that, then add further echo statements after each line to see how far it gets before failing.

Ah. Nothing is generated.  I wonder why the earlier test script worked, but this one doesn't?

---

### Post by dcstar on 2009-09-19
> **Mander said:**
> I had just left those other two for the time being, but I've changed it now.

Crontab now reads:
```

MAILTO=""
USER=amandav
HOME=/home/amandav
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/home/amandav/bin:/media/DATA/AmandaV/Docume$
DISPLAY=:0.0

09 01 * * * /media/DATA/AmandaV/Documents/Scripts/ThesisDailyBack > /media/DATA$
20 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupFiles > /dev/null$
30 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupTables >/dev/null$
40 21 * * 5 /media/DATA/AmandaV/Documents/Scripts/WeeklyBackupImages >/dev/null$
* * * * * date >> /home/amandav/crontest.log
```

But it still doesn't work.

Why is the crontab file full of shell commands?

The crontab file is a list of scheduled jobs, not a shell script.

---

### Post by pcjunkie on 2009-09-20
> **muteXe said:**
> "Tearing my hair out over cron job" would make an excellent song title.

Don't give Nickelback ideas..

---

### Post by Mander on 2009-09-21
> **dcstar said:**
> Why is the crontab file full of shell commands?

The crontab file is a list of scheduled jobs, not a shell script.

I guess I don't understand the question. As you might have gathered I'm not very experienced with this sort of thing.

I copied an example from someplace (who knows where now) and modified it.  

What I want it to do is run some scripts at certain times of the day and week that make .tar files from a list of files and email them to my google account.  It's an easy and free way for me to make off-site backups of my PhD thesis.  If there is a different way to do this besides cron, please enlighten me.

---

### Post by DaithiF on 2009-09-23
I'm pretty much out of suggestions ... if it were me the next thing I would try would be moving the script to my home dir ... i see that its on an external drive/partition at the moment -- bit of a long shot but in case there is some problem accessing/executing from that mounted drive when being run by cron.

---

### Post by Mander on 2009-10-23
> **DaithiF said:**
> I'm pretty much out of suggestions ... if it were me the next thing I would try would be moving the script to my home dir ... i see that its on an external drive/partition at the moment -- bit of a long shot but in case there is some problem accessing/executing from that mounted drive when being run by cron.

Just thought I'd update this to say that this didn't work either.  I have my computer in three main partitions, one of which is a shared data partition (dual boot Vista/Ubuntu).  The scripts are in the data partition, so I tried both the actual /media location and the /home symbolic link.  I also tried moving them to /home itself, and it didn't make any difference.

---

