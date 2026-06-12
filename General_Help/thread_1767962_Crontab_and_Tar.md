---
title: "Crontab and Tar"
date: 2011-05-26
forum: General Help
---

### Post by chaotixmonjuish on 2011-05-26
I have created an automated backup using the following:

```

today=$(date '+%d_%m_%y')

```and crontab

```

00 11 * * * tar -czf /home/josh/Desktop/archive-"$today".tar /home/josh/Desktop/File/

```When cron runs it creates a .tar like it is suppose to, but it creates archive-.tar.  However, when I manually type in that command, I get archive-"whateverthedateis".

Is there a step that I missed since the date keeps being omitted by this cronjob.

I tried a another method
```

10 12 * * * tar -cf /home/josh/Desktop/File-`date +%Y-%m-%d`.tar.gz /home/josh/Desktop/File

```

I then checked syslog

```

May 26 12:11:02 desktop CRON[8536]: (josh) CMD (tar -cf /home/josh/Desktop/File-`date +)
May 26 12:11:02 desktop CRON[8534]: (CRON) error (grandchild #8536 failed with exit status 2)
May 26 12:11:02 desktop CRON[8534]: (CRON) info (No MTA installed, discarding output)

```

---

### Post by mbeierl on 2011-05-26
Unfortunately you are mixing up crontab execution instructions with scripting languages.  The crontab file does not interpret anything, but runs exactly what is put in it, so the `date` or "$today" are not interpreted.

What you might want instead is a shell script in your home directory called "archive.sh" that contains
```
tar -czf /home/josh/Desktop/archive-`date +%Y-%m-%d`.tar /home/josh/Desktop/File/
```
and then your crontab would have:
```
00 11 * * * /home/josh/archive.sh
```

Does that make sense?

---

### Post by hwttdz on 2011-05-26
I think you could also do "export today=`date +%Y-%m-%d`; tar -czf files $today.tar.gz"  The important thing is getting the date stored in the variable today in the environment that is running the command.

---

### Post by Habitual on 2011-05-26
create a file called joshbup.sh and stick this in it.
```

#!/bin/bash
today=$(date '+%d_%m_%y')
tar -czf /home/josh/Desktop/archive-"$today".tar.gz /home/josh/Desktop/File/
exit 0

```
Save it (to /home/josh/ for now)

Open a terminal:
```
chmod 700 /home/josh/joshbup.sh
```

cron:
```

00 11 * * * /home/josh/joshbup.sh /dev/null 2>&1

```

"/dev/null 2>&1" is required until you install or (re)configure a c-li mail client such as mailx. ("No MTA installed, discarding output")

P.S. Your command tar -czf /home/josh/Desktop/archive-"$today".tar is incorrect without a .gz extension (compression).
tar -czf /home/josh/Desktop/archive-"$today".tar.**gz** is a correct format for a tar -**z** switch.

If you don't want/need/like a .gz extension, then remove "z" from "tar czf" in the joshbup.sh file.

Hope that helps. :)

---

