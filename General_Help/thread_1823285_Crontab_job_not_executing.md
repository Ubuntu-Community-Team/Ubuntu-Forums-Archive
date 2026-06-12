---
title: "Crontab job not executing"
date: 2011-08-11
forum: General Help
---

### Post by tarun86 on 2011-08-11
Hi Everyone

I am a xfce user. I have a list of wallpapers and I wanted to change them every 5 minutes

Initially I was using a simple command in crontab entry to change it, 
> */5 * * * * xfdesktop --reload
it was working but it would crash xfdesktop process after few changes and the screen would be all grey. To solve this issues I wrote a simple script which would check if xfdesktop is alive and if yes it would call **xfdesktop --reload** else start **xfdesktop**

I called this script idesktop & its path is ~/.bin/idesktop

> #!/bin/bash
APPCHK=$(/bin/ps -A | /bin/grep -c xfdesktop)
if [ $APPCHK = '1' ]
then
	/usr/bin/xfdesktop --reload
else
	/usr/bin/xfdesktop
fi

my crontab entry for this script
> */5 * * * * /home/xmonkee/.bin/idesktop

This would give me this error. Any ideas because I am out of them. Path variable has been updated to include ~/.bin in it.
I have tried lots of permutations and combinations but nothing seem to work, executing the script in terminal is working perfectly fine
> Aug 12 06:59:01 xmonkee-U-100 CRON[1836]: (xmonkee) CMD (/home/xmonkee/.bin/idesktopp )
Aug 12 06:59:01 xmonkee-U-100 CRON[1834]: (CRON) error (grandchild #1836 failed with exit status 127)
Aug 12 06:59:01 xmonkee-U-100 CRON[1834]: (CRON) info (No MTA installed, discarding output)

---

### Post by SoFl W on 2011-08-11
I will have to look for it, (someone else just asked me as well) you can create an XML file to change the backgrounds.  That doesn't answer your question, but it will help your quest.
[B]
EDIT:[/B]
Check out these threads:
[http://ubuntuforums.org/archive/index.php/t-1395112.html](http://ubuntuforums.org/archive/index.php/t-1395112.html)
[http://ubuntuforums.org/showthread.php?t=1410618](http://ubuntuforums.org/showthread.php?t=1410618)

---

### Post by Habitual on 2011-08-11
you need to install a mail utility like mailx
"...No MTA installed..."

cron error/output/log says
".../home/xmonkee/.bin/ideskto**pp** )" 2 Ps

Check that.

Is /home/xmonkee/.bin/idesktop[p] executable?
Terminal > 
```
chmod 700 /home/xmonkee/.bin/idesktop[p]
```

if it is not.

---

### Post by tarun86 on 2011-08-11
@Habitual - Sorry about that silly mistake but its still not working

> Aug 12 07:31:01 xmonkee-U-100 CRON[3577]: (xmonkee) CMD (/home/xmonkee/.bin/idesktop )
Aug 12 07:31:01 xmonkee-U-100 CRON[3576]: (CRON) error (grandchild #3577 failed with exit status 1)

EXIT status 1: states something like error involving division by 0 or something similar but this is simple script where nothing of that sort is involved. I have tried including the whole path of the "grep", "ps", "idesktop".

/bin/bash is the shell in /etc/crontab

PATH variable is update to include ~/.bin

and still it gives me this silly error. 

Is there a way to get output of crontab execution ?

---

### Post by tarun86 on 2011-08-11
> **SoFl W said:**
> I will have to look for it, (someone else just asked me as well) you can create an XML file to change the backgrounds.  That doesn't answer your question, but it will help your quest.
[B]
EDIT:[/B]
Check out these threads:
[http://ubuntuforums.org/archive/index.php/t-1395112.html](http://ubuntuforums.org/archive/index.php/t-1395112.html)
[http://ubuntuforums.org/showthread.php?t=1410618](http://ubuntuforums.org/showthread.php?t=1410618)

Thanks man. Let me have a look and get back to you

I dont have gnome on my machine. Just fluxbox & xfce, it was tiny notebook, just want to keep it light & easy

---

### Post by Toz on 2011-08-11
> **tarun86 said:**
> Hi Everyone

I am a xfce user. I have a list of wallpapers and I wanted to change them every 5 minutes

Initially I was using a simple command in crontab entry to change it, 

it was working but it would crash xfdesktop process after few changes and the screen would be all grey. To solve this issues I wrote a simple script which would check if xfdesktop is alive and if yes it would call **xfdesktop --reload** else start **xfdesktop**

I called this script idesktop & its path is ~/.bin/idesktop



my crontab entry for this script


This would give me this error. Any ideas because I am out of them. Path variable has been updated to include ~/.bin in it.
I have tried lots of permutations and combinations but nothing seem to work, executing the script in terminal is working perfectly fine

cron won't know about your desktop display. Try pre-pending **DISPLAY=:0.0** in front of your xfdesktop command like this:
```
DISPLAY=:0.0 /usr/bin/xfdesktop --reload
```

---

### Post by tarun86 on 2011-08-11
@Tozz

That was brilliant & worked perfectly. Thanks for that

1 more doubt: Why was this command executing then ? As I mentioned, I was using this command which was causing xfdesktop to crash after sometime. This included no display information.

> */5 * * * * xfdestop --reload

---

### Post by Toz on 2011-08-11
Good question. I can't get that cron command to work on my system at all (because of the display issue). Is it possible that you had another process/thread running that was switching the backgrounds while you were testing the cron job? I know this happened to me when I was figuring it out.

---

### Post by tarun86 on 2011-08-11
Nopes, this was the first command/cronjob that I tried with no other process  handling wallpaper changing. Since it worked(with no display info provided to it) w/o any problem before crashing the xfdesktop by 10-15 changes of wallpaper. Its the crash of xfdesktop process that made me switch to the above mentioned script. 

Anyways certainly will keep this thing in mind from now onwards.

---

