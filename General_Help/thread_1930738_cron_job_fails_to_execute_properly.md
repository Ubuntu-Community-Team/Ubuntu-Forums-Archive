---
title: "cron job fails to execute properly"
date: 2012-02-24
forum: General Help
---

### Post by Thorsen V on 2012-02-24
I have been trying to put together a script that basically changes the wallpaper at certain times. Quite silly: I have two images, one is a daylight artwork, the other is the same scene at night time. Anyway ....

Reducing the problem to it's simplest, I cannot get the following fragment to work when it is added to crontab:
[INDENT][FONT=Courier New]#!/bin/sh[/FONT]
[FONT=Courier New]/usr/bin/gconftool-2 --type string --set  /desktop/gnome/background/picture_filename '/home/other/Pictures/Wallpapers/DigitalBlasphemy/citadelnight11920.jpg'[/FONT]
[/INDENT]Of course it works properly if I run the script directly.

I'm looked at the advice for using crontab that is available, so I've tried things like adding: 
[INDENT][FONT=Courier New]SHELL=/bin/bash
[/FONT][FONT=Courier New]PATH=/usr/sbin:/usr/bin:/sbin:/bin
[/FONT][/INDENT]to the crontab. I've even tried adding:
[INDENT][FONT=Courier New]export DISPLAY:=0[/FONT]
[/INDENT]to the script, even though I don't believe is necessary for gconftool-2.

I've tried specifying gconftool-2 as:
[INDENT][FONT=Courier New]/usr/bin/gconftool-2[/FONT]
[/INDENT]But nothing I've tried works.

The script is definitely called (I've got echo messages to file that go off), and as far as I can tell gconftool-2 itself is called (I redirect stder/stdout from the command and the output file is zero-length).

Fpr some reason -- it seams -- gconftool-2 isn't updating the system when it's  a cron job. But does if the script is run properly.

Any help would be appreciated.

---

### Post by Azdour on 2012-02-24
Hi,

I wonder if when its run via the crontab you have to specify the users config location?

gconftool-2 --config-source=xml::/home/username/.gconf

---

### Post by forrestcupp on 2012-02-24
I wonder if you need to set the script's permissions to run as an executable.

---

### Post by Thorsen V on 2012-02-24
> **forrestcupp said:**
> I wonder if you need to set the script's permissions to run as an executable.
Thanks for the reply forrestcupp.
No, the execute permission is set (the script works fine in a terminal etc)

---

### Post by Thorsen V on 2012-02-24
> **Azdour said:**
> Hi,

I wonder if when its run via the crontab you have to specify the users config location?

gconftool-2 --config-source=xml::/home/username/.gconf
That was a great idea Azdour and I thought you must be right, but no, it still doesn't run out of crontab.

It finally occurred to me to test the exit status (I'm a bit rusty at shell scripting).

gconftool returns an exit code of 1 when the job fails in cron; it's 0 when it succeeds in a terminal.

There doesn't seem to be anything in the man page about the meaning of exit code(s) with gconftool though :(

I've expended a ridiculous amount of time on this stupid thing :)

---

### Post by forrestcupp on 2012-02-24
> **Thorsen V said:**
> Thanks for the reply forrestcupp.
No, the execute permission is set (the script works fine in a terminal etc)

I didn't think that was it, but it was worth a shot. If you run a script in the terminal using the 'sh' command, the execute permission doesn't have to be set for it to work.

I thought Azdour had to have been right, too.

---

### Post by Derek Karpinski on 2012-02-24
Check out this thread:
 
[http://ubuntuforums.org/showthread.php?t=1905699](http://ubuntuforums.org/showthread.php?t=1905699)

---

### Post by Thorsen V on 2012-02-24
Thank you Derek.

Actually I found the problem by resorting to brute force :)

I dumped the ENTIRE env into crontab (!) and the script started working ...

Paring it down I eventually discovered that these 2 lines seem to be all that's needed:
[INDENT][FONT=Courier New]SHELL=/bin/bash[/FONT]
[FONT=Courier New]DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-oITyT9ge0M,guid=f49eb8822e538b$[/FONT]
[/INDENT]No idea what that DBUS_SESSION_BUS_ADDRESS is about and perhaps the string is specific to my box but anyway, hopefully it can help others experiencing similar problems.

Thanks :)

---

### Post by Thorsen V on 2012-02-24
My desktop by day:

[[IMG]http://img820.imageshack.us/img820/2007/daythumb.jpg[/IMG]]("http://img546.imageshack.us/img546/3364/dayo.jpg")

And my desktop by night:
[[IMG]http://img827.imageshack.us/img827/3199/nightthumb.jpg[/IMG]]("http://img39.imageshack.us/img39/483/nighten.jpg")

Silly but fun. 
Next I might try linking in some way to the local sunrise & sunset times ... that way I'll know when it's dark (or dawn) without going to the trouble of looking out of the window :mrgreen:

---

### Post by forrestcupp on 2012-02-24
That's pretty awesome. That's a great idea. There really should be an easier way to do things like that.

What is that picture from, by the way?

---

### Post by Thorsen V on 2012-02-24
> **forrestcupp said:**
> That's pretty awesome. That's a great idea. There really should be an easier way to do things like that.

What is that picture from, by the way?

it's from [http://digitalblasphemy.com/](http://digitalblasphemy.com/)

Unfortunately you need to be a member, but it's quite inexpensive :)

---

### Post by Thorsen V on 2012-03-25
> **Thorsen V said:**
> Thank you Derek.

Actually I found the problem by resorting to brute force :)

I dumped the ENTIRE env into crontab (!) and the script started working ...

Paring it down I eventually discovered that these 2 lines seem to be all that's needed:[INDENT][FONT=Courier New]SHELL=/bin/bash[/FONT]
[FONT=Courier New]DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-oITyT9ge0M,guid=f49eb8822e538b$[/FONT]
[/INDENT]No idea what that DBUS_SESSION_BUS_ADDRESS is about and perhaps the string is specific to my box but anyway, hopefully it can help others experiencing similar problems.

Thanks :)
Just to properly bring this up to date ...

As it stands the above DOES NOT properly fix the problem. This is because each time the machine is booted the value of the env variable [FONT=Courier New]DBUS_SESSION_BUS_ADDRESS [/FONT]gets set to a new "guid" which then breaks the cron job again ...

I guess a possible fix is to run a script at startup that rewrites the cron file, removing the expired value and adding the new ... or just run a script that does cron's job by simply 'sleep'ing for ten minutes periods through till the next reboot :)

I'm annoyed though that there isn't a "reasonable" way to do this using the built in mechanism. 

I guess the author of the env variable has a good reason why it works like that ...
[FONT=Courier New]
[/FONT]

---

### Post by redmk2 on 2012-03-25
> **Thorsen V said:**
> Just to properly bring this up to date ...

As it stands the above DOES NOT properly fix the problem. This is because each time the machine is booted the value of the env variable [FONT=Courier New]DBUS_SESSION_BUS_ADDRESS [/FONT]gets set to a new "guid" which then breaks the cron job again ...

I guess a possible fix is to run a script at startup that rewrites the cron file, removing the expired value and adding the new ... or just run a script that does cron's job by simply 'sleep'ing for ten minutes periods through till the next reboot :)

I'm annoyed though that there isn't a "reasonable" way to do this using the built in mechanism. 

I guess the author of the env variable has a good reason why it works like that ...
[FONT=Courier New]
[/FONT]

I think all you would need to do is provide the fresh (current) variable in the script.  I don't do a lot of this so others will surely improve upon this example.  

You can add the variable $GUID like like this```

#!/bin/bash
# extracts the current variable for guid.
GUID=$DBUS_SESSION_BUS_ADDRESS

```

If you only needed the last part (after the ,) you could do something like this```
#!/bin/bash

# Extracts the var $GUID to an array and prints 
# the 2nd element of the array (array = 0,1)
GUID=$DBUS_SESSION_BUS_ADDRESS
OIFS=$IFS
IFS=','
GUID_array=($GUID)
IFS=$OIFS
echo ${GUID_array[1]}

```

I'd like to see your entire script if you don't mind.

---

### Post by Cheesehead on 2012-03-25
The dbus variable is required because it tells gconf which user's settings you are talking about.

In theory, $DBUS_SESSION_BUS_ADDRESS should also change each time you logout/login. It's specific to each user's session, which is why it changes.

Cron's limited (for your protection) environment simply doesn't know which display or dbus session you're talking about, since it doesn't have access to each user's environment variables unless you specifically export them.

redmk2 is on the right track by detecting and passing the variable.

In Unity and Gnome3, use [http://askubuntu.com/questions/66914/how-to-change-desktop-background-from-command-line-in-unity](http://askubuntu.com/questions/66914/how-to-change-desktop-background-from-command-line-in-unity) instead of gconf.

---

### Post by Thorsen V on 2012-03-25
> **redmk2 said:**
> I think all you would need to do is provide the fresh (current) variable in the script.

:)
That's missing the point: When the script runs (from cron) there is no "fresh (current) variable" ...

This is why the variable needs to be defined in the crontab, becoming part of the cron environment that is then passed to the child process; and crontab needs to be rewritten each time there's a boot/log-in (because the variable changes each session)

Of course I can write a script that rewrites crontab each time the machine boots, but if I have to add something to the Startup Applications to get this to work, I might just as well do something simpler and a lot less dangerous: write a script that just runs in the background all the time (and checks inside a loop with a "sleep 600" say)

 (actually that's exactly what I had before I decided to try to do it the "right way" and it worked just fine :))

> **redmk2 said:**
> 
I'd like to see your entire script if you don't mind.

[#1]("http://ubuntuforums.org/showpost.php?p=11714224&postcount=1")
  2 lines. It's that simple.

Of course I could add a script to Startup Applications that does something like:
```

crontab - << HERE
# m h  dom mon dow   command
SHELL=/bin/bash
DBUS_SESSION_BUS_ADDRESS=$DBUS_SESSION_BUS_ADDRESS

*/20 * * * * /home/Thorsen/Apps/printIP
*/10 * * * * /home/Thorsen/Apps/wallpaper.am.pm.sh
*/30 * * * * /home/Thorsen/Apps/linuxoutlawschecker

HERE

```And try not to forget that's how crontab works on this machine :)

---

