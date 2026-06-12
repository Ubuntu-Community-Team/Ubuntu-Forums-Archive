---
title: "Crontab won't run jobs"
date: 2010-09-10
forum: General Help
---

### Post by Xinerama on 2010-09-10
Here's my crontab entry as a normal user. Ubuntu 10.4 Lucid Lynx
```

SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
MAILTO=""

30 07 * * * export DISPLAY=:0.0 && /usr/local/bin/ChangeGTKTheme
30 19 * * * export DISPLAY=:0.0 && /usr/local/bin/ChangeGTKTheme

@reboot export DISPLAY=:0.0 && /usr/local/bin/ChangeGTKTheme

```
Here's my ChangeGTKTheme script.
```

#!/bin/bash
# /usr/local/bin/ChangeGTKTheme
set -x 	#shell debugger
echo "*********Beginning of script**************"
TIME=`/bin/date +%H`

#Wait a minute to make sure everything's loaded
#/bin/sleep 60

#Check the date and make changes as necessary
if [ "$TIME" -ge 7 ] && [ "$TIME" -le 18 ] ; then
	gconftool-2 --type string --set /apps/metacity/general/theme "Kin" && gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Kin" && gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "Kin"
	gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close" 
else
	gconftool-2 --type string --set /apps/metacity/general/theme "Ambiance" && gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Ambiance" && gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "Ambiancename"
	gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close" 
fi
echo "**********End of script*****************"


```

I had it piping the output to a file on my desktop which it would do, but it never changed the "look or theme" of the desktop.

It works if I reboot but only IF, never any other time. :(
I've tested cron with "xmessage hello" and that works fine, but nothing else.
What should I do?

---

### Post by ubulal on 2010-09-10
Are you sure you're *not* already having the "Kin" theme set between 7:00 and 18:59, so you could actually see a change?  The same for the Ambience theme between 19:00 and 6:59.

Does setting the values with gconftool-2 have an immediate effect, i.e. can you see a change in widget style when running the script in a terminal directly? (I'm not running GNOME currently, so cannot test myself.)

Is your machine running for some time before 7:30 and 19:30?

Is there a message in /var/log/syslog that cron executed your script at 7:30 or 19:30?

Just some things I'd check...

---

### Post by Xinerama on 2010-09-10
> 
Are you sure you're *not* already having the "Kin" theme set between 7:00 and 18:59, so you could actually see a change? The same for the Ambience theme between 19:00 and 6:59.

Yes, I'm sure.  I frequently just leave the computer on seeding torrents.  :D
> 
Does setting the values with gconftool-2 have an immediate effect, i.e. can you see a change in widget style when running the script in a terminal directly? (I'm not running GNOME currently, so cannot test myself.)

Yes, it does.  I just tested it (it's 10:30 A.M.) and it changed the theme from Ambiance to Kin.
> Is your machine running for some time before 7:30 and 19:30?
Yes.
> Is there a message in /var/log/syslog that cron executed your script at 7:30 or 19:30?
Here's the output:
```

grep -r 'cron' /var/log/syslog
Sep 11 01:20:13 elias-desktop anacron[988]: Job `cron.daily' terminated
Sep 11 01:20:13 elias-desktop anacron[988]: Normal exit (1 job run)
Sep 11 02:17:01 elias-desktop CRON[3566]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 03:17:01 elias-desktop CRON[3683]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 04:17:01 elias-desktop CRON[3762]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 05:17:01 elias-desktop CRON[4507]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 06:17:01 elias-desktop CRON[4601]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 06:25:01 elias-desktop CRON[4620]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
Sep 11 07:17:01 elias-desktop CRON[4885]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 07:30:01 elias-desktop CRON[4903]: (root) CMD (start -q anacron || :)
Sep 11 07:30:01 elias-desktop anacron[4909]: Anacron 2.3 started on 2010-09-11
Sep 11 07:30:01 elias-desktop anacron[4909]: Normal exit (0 jobs run)
Sep 11 08:17:01 elias-desktop CRON[4974]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep 11 09:17:01 elias-desktop CRON[5111]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```
It's not running the script at all, and I don't believe there's a problem with it.  If I put it in /etc/crontab what would be the format? (I think it's going to be different because /etc/crontab uses /bin/sh and overall the layout looks much different from my crontab.)

---

### Post by ubulal on 2010-09-10
You've grep'ed syslog only for lines with lower case "cron".  Could you repeat that with -i instead of -r?

---

### Post by dcstar on 2010-09-11
> **Xinerama said:**
> Here's my crontab entry as a normal user. Ubuntu 10.4 Lucid Lynx
[CODE]
SHELL=/bin/bash
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
MAILTO=""

30 07 * * * export DISPLAY=:0.0 && /usr/local/bin/ChangeGTKTheme
30 19 * * * export DISPLAY=:0.0 && /usr/local/bin/ChangeGTKTheme
...........

So the crontab daemon executes "export DISPLAY=:0.0", waits for that to finish running, **then probably closes that shell** and then executes "/usr/local/bin/ChangeGTKTheme"?

Don't separate related commands, put them in a single script so you **know** that they are run together.

---

### Post by Xinerama on 2010-09-11
Here's the result with the "-i" option, but it didn't change the theme.
```

Sep 11 07:30:01 elias-desktop CRON[4904]: (elias) CMD (export DISPLAY=:0.0 && /usr/local/bin/ChangeGTKTheme)

```
~~dcstar, I took out "export DISPLAY=:0.0 &&" from crontab and placed it in my script as such.
I hope this works.  I'll find out soon enough.

```

#!/bin/bash
# /usr/local/bin/ChangeGTKTheme
set -x 	#shell debugger
echo "*********Beginning of script**************"
TIME=`/bin/date +%H`

#Wait a minute to make sure everything's loaded
#/bin/sleep 60

#Check the date and make changes as necessary
if [ "$TIME" -ge 7 ] && [ "$TIME" -le 18 ] ; then
	[COLOR="DarkGreen"]export DISPLAY=:0.0 &&[/COLOR] gconftool-2 --type string --set /apps/metacity/general/theme "Kin" && gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Kin" && gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "Kin"
	gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close" 
else
	[COLOR="DarkGreen"]export DISPLAY=:0.0 &&[/COLOR] gconftool-2 --type string --set /apps/metacity/general/theme "Ambiance" && gconftool-2 --type string --set /desktop/gnome/interface/gtk_theme "Ambiance" && gconftool-2 --type string --set /desktop/gnome/interface/icon_theme "Ambiance"
	gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close" 
fi
echo "**********End of script*****************"

```

---

### Post by ubulal on 2010-09-11
> **dcstar said:**
> So the crontab daemon executes "export DISPLAY=:0.0", waits for that to finish running, **then probably closes that shell** and then executes "/usr/local/bin/ChangeGTKTheme"?

No.  Everything after the fifth field will be executed as a single command by cron.  x && y is a list and executed in the same shell environment.

Although I'm not sure if gconftool-2 even needs DISPLAY set.  I'd think it just manipulates the gconf database of the user id which it executes.  So export DISPLAY=:0.0 is probably superfluous here. -- Yep, this works, so DISPLAY is not needed:

```

unset DISPLAY; gconftool-2 --all-dirs /apps

```

---

### Post by ubulal on 2010-09-11
Interesting, it's more complicated than we thought. See here for the solution (most probably):
[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/285937](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/285937)

---

### Post by Xinerama on 2010-09-11
I knew I wasn't the first to want to do this. 
Thanks for the tip.  At any rate in about an hour and a half I'll know for sure.  I went ahead and took out the DISPLAY references.  Thanks.

---

### Post by john newbuntu on 2010-09-11
I played around with your scripts a bit and with ubulal's advice, found it a way to get it to work.  Since gconf depends on dbus.

Keep your crontab really simple like:
```
30 07 * * * /usr/local/bin/ChangeGTKTheme
```Now, in your ChangeGTKTheme script, add the following right after you echo "Beginning of script":

```
source `ls -t /home/<userid>/.dbus/session-bus/* | head -1`
export DBUS_SESSION_BUS_ADDRESS
```That's it.  It worked for me.  That variable is not available at the time cron gets to run it, which is why you either need to start a message bus every time which is a pain or just use its current variable from your config.

EDIT: This may not be the best way, but see if you can find one simpler.

---

### Post by Xinerama on 2010-09-11
Thank you so much!  Finally, it worked.  I just don't understand this part of course.
```
That variable is not available at the time cron gets to run it, which is why you either need to start a message bus every time which is a pain or just use its current variable from your config.
```

So you're saying the TIME variable that I declared in the script is not available to cron.  Okay....I kind of understand.  I think. :-k Basically, cron doesn't know what time it is (oxymoronic) or my script doesn't have the time to tell cron what time it is?  Hmmm!? :neutral:
Either way, it worked and thank you

---

### Post by john newbuntu on 2010-09-11
Not the TIME variable.  That one is fine.  But the DBUS_..whatever variable was the problem. Gconf at one point was using CORBA platform APIs for communication and was then moved to Dbus as the latter is a lighter-weight protocol. 

So your script needed to know the dbus variables which are not by default present in your environment because you need to start a session bus every time.

Since gconf works over dbus and can be started with the dbus-launch command, it will leave you with several dbus daemons hanging all over the place once you make theme changes.  So one way to avoid it is to query the current session bus variables and make it available to the script.

NOTE: Cron DOES know exactly what time it is.

---

