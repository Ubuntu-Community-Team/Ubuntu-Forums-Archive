---
title: "Cron / Alarm Clock"
date: 2011-06-13
forum: General Help
---

### Post by Atrom on 2011-06-13
So, I'm attempting to write an alarm clock from scratch without a GUI, doing this through a bash script.

So far I wrote the file that actually iniates the song, and I was trying  to set up a crontab so I could do it at a certain time, making it  function like an alarm clock, but it isn't seeming to work, any input on  why

```
SHELL=/bin/bash
12 5 *   *   *   /home/angelo/music.sh
``` That is my crontab

Any help is greatly appreciated!

---

### Post by Atrom on 2011-06-13
More to the point, does anyone have any advice on what I can do to the chrontab to make it initiate the script?

---

### Post by syrex314 on 2011-06-13
Have you installed your table with crontab? You can double-check the currently installed crontab with:

```
crontab -l
```

---

### Post by Atrom on 2011-06-13
When I do Crontab -l it shows the event and the time, but when the time occurs the script simply doesn't start.

---

### Post by ruffEdgz on 2011-06-13
Can you make sure that the crontab logs are enabled in your /etc/rsyslog.d/50-default.conf file (edit that file and look for the following line and make sure its uncommented)
```
cron.*                          /var/log/cron.log
```
Restart rsyslogd if you needed to uncomment that line:
```
sudo service rsyslog restart
```
Doing this will help understand more about what is happening when that file is ran at 5:12am (a log should be created in /var/log/crontab)

Can you run the following command and reply back with the answer:
```
ll /home/angelo/music.sh
```
Also, placing the code on this post wouldn't be bad either to see what commands you are trying to use:
```
cat /home/angelo/music.sh
```
Cheers!

---

### Post by Atrom on 2011-06-13
Fixed the read-only problem
Reply to your post below:

Will do, to double check commenting in bash is done through # right? So if it looks like

#cron.*                /var/log/cron.log

it is commented right? because thats what it has, I'll take the hash out and restart it.

Did the latter.

when I did ll it said "command ll not found"

my script is really simple, it's as follows
```

#!/bin/sh
aplay 3.wav

```3.wav is a song on my PC (although you knew that I'm sure.)

EDIT: /FACEPALM I was running it at 12 5 * * * expecting results when it's 5:12 PM, my bad...

EDIT2: even after adressing that, and fixing it along with doing the fixes you offered it still isn't working, although the ll command never did work.

---

### Post by Cheesehead on 2011-06-13
1) Test cron.

* * * * * touch /tmp/tempfile

If the tempfile gets created, then cron is working fine.
You can also check /var/log/syslog for the cron.hourly job.

Usually in these situations cron is working fine.

2) Check your script. Cron runs in a limited environment - it doesn't know (or care) where you want the music piped to...unless you specifically tell it. You may need to insert some debug flags in your script to prove it's running and trace the breakage.

Or just post it here.

---

### Post by Atrom on 2011-06-13
I made a Cronfile.txt 
Crontab'd it
checked the log it was set at
* * * * * touch tmp/tempfile

Nothing appeared :3 I also posted my script above.

---

### Post by Habitual on 2011-06-14
> **Atrom said:**
> Fixed the read-only problem
Reply to your post below:

Will do, to double check commenting in bash is done through # right? So if it looks like

#cron.*                /var/log/cron.log

it is commented right? because thats what it has, I'll take the hash out and restart it.

Did the latter.

when I did ll it said "command ll not found"

my script is really simple, it's as follows
```

#!/bin/sh
aplay 3.wav

```3.wav is a song on my PC (although you knew that I'm 


Try aplay /path/to/3.wav in your script.

---

### Post by ruffEdgz on 2011-06-14
> 
Try aplay /path/to/3.wav in your script.

To add on to Habitual's comment, lets add this to your script:
```

#!/bin/sh
/usr/bin/aplay /path/to/3.wav

```

For that 'll' command that didn't work, try this:
```
ls -l /home/angelo/music.sh
```
Just wanted to see what your file looked like with permissions.

If you did the rsyslog change and restart, you should be able to look into a file located:
```

sudo less /var/log/crontab
```
This file will give you a better idea of what is happening with your crontab. Search that and any other files related to it (/var/log/crontab.1, etc...) and if there is anything eventful in there, post some of those lines here.

Cheers!

---

### Post by Habitual on 2011-06-14
Thanks ruffEdgz for the assist. :)

---

### Post by Atrom on 2011-06-14
Hey guys, I appreciate all the help, but today when I tried to turn my Ubuntu box on I was greeted by an error message, through troubleshooting I think I've determined the Hard drive is fried :|

---

### Post by Habitual on 2011-06-14
Bummer. :(

---

### Post by Atrom on 2011-06-15
Yeah, but I'll promptly be buying / reformatting some old drive of mine, and back on ubuntu in no time :)

---

### Post by Atrom on 2011-06-15
Quick question, since I'll be back on ubuntu within hours, where you said /path/to/3.wav do I fill /path/to/ with the path, example being /home/angelo/3.wav?

---

