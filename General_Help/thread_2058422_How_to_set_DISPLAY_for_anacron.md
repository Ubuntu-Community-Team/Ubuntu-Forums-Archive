---
title: "How to set DISPLAY for anacron"
date: 2012-09-15
forum: General Help
---

### Post by Ralph L on 2012-09-15
I am trying to run a script periodically using anacron (so it will be executed when the computer starts up, if computer was down at the scheduled run time).  The script uses zenity to ask a question of the user.  However, I can't get zenity to display on my screen, when I am logged in as user "ralph".  I suspect this is because anacron doesn't know for what user the script is being run.  Currently my /etc/anacrontab entry is:

```

1	1	lbtest	DISPAY=:0.0 && /home/ralph/lbtest
```

I suspect that I don't have the correct setting for DISPLAY, that it needs to know for what user to do the displaying.

Any help appreciated.

Thank you

---

### Post by spjackson on 2012-09-15
I don't think you need && but I'm not sure whether using && is actually an error. What is an error is that you have missed an L out of DISPLAY.

---

### Post by Ralph L on 2012-09-15
spjackson

First, thank you for replying. Then thank you for correcting my stupid error.  However, it still didn't work.  I even took out the && that I had between the two commands so it now reads:

```
1	2	lbtest	DISPLAY=:0.0 /home/ralph/lbtest
```

syslog shows that the lbtest executed without error.  It just does not display the zenity question.  Maybe anacron won't work for single user, since there is nothing in the the command to specify a specific user.  I thought maybe there was a DISPLAY parameter to set the user for the command, but all I could find was how to set the DISPLAY to a machine, not to a machine plus a particular user.

Any other thoughts?

---

### Post by steeldriver on 2012-09-15
I wonder if it's an Xauthority thing?

The following post suggests using xhost - you could try that just to check if it *is* an authority issue:

[http://askubuntu.com/questions/102296/how-to-run-gui-app-from-cron-as-root](http://askubuntu.com/questions/102296/how-to-run-gui-app-from-cron-as-root)

however the 'right' (more secure) way to fix it might be to copy the user's .Xauthority magic cookie to root via xauth I think:

[http://www.losurs.org/docs/tips/x11/root-x](http://www.losurs.org/docs/tips/x11/root-x)

---

### Post by dcstar on 2012-09-16
> **Ralph L said:**
> 
.........
Any help appreciated.

Thank you

[http://ubuntuforums.org/showthread.php?t=185993](http://ubuntuforums.org/showthread.php?t=185993)

---

### Post by Ralph L on 2012-09-17
Still no satisfaction.  Still can't make it work.  I changed my test script to something I call loggertest, and I kind of got sendmail to work so I can get better error messages.  Here is my test script:

```
#! /bin/bash
logger loggertest9

export DISPLAY=:0

logger "Reached zenity command"
zenity --question --text "loggertest9 click yes or no"
# If the person said cancel, then tell them. If they said ok, then tell them that.
if [ "$?" == "1" ] ; then
    logger "You clicked cancel."
    exit
fi
if [ "$?" == "0" ] ; then
    logger "You clicked OK."
    exit

else logger "Input was neither a 0 nor a 1.  Something is wrong."
exit 1
fi
```

Here is the line in /etc/anacrontab that calls it:

```
1	2	loggertest9	export DISPLAY=:0 && /home/ralph/loggertest9
```

Here is the email that anacron sent about my problem.  Looks to me like the "export DISPLAY=:0" (no quotes) didn't work, causing zenity to bomb.  Note that I have "export DISPLAY=:0 in two places.  I have tried it in both places by themselves, but didn't make a difference.  Also note that the first two "logger" messages successfully went to the syslog file, before the bombing at zenity.  The code box for the email below stretches way to the right to get the whole error message in.

```
From root@ralph-Latitude-D610.local  Mon Sep 17 16:25:17 2012
Return-Path: <root@ralph-Latitude-D610.local>
Received: from ralph-Latitude-D610.local (localhost [127.0.0.1])
	by ralph-Latitude-D610.local (8.14.4/8.14.4/Debian-2ubuntu2) with ESMTP id q8HNPH7Q001926
	for <root@ralph-Latitude-D610.local>; Mon, 17 Sep 2012 16:25:17 -0700
Received: (from root@localhost)
	by ralph-Latitude-D610.local (8.14.4/8.14.4/Submit) id q8HNPHKK001925
	for root; Mon, 17 Sep 2012 16:25:17 -0700
Date: Mon, 17 Sep 2012 16:25:17 -0700
Message-Id: <201209172325.q8HNPHKK001925@ralph-Latitude-D610.local>
From: Anacron <root@ralph-Latitude-D610.local>
To: root@ralph-Latitude-D610.local
Subject: Anacron job 'loggertest9' on ralph-Latitude-D610

No protocol specified
No protocol specified

(zenity:1921): Gtk-WARNING **: cannot open display: :0

** (zenity:1921): WARNING **: Command line `dbus-launch --autolaunch=8a4d67b9735614b1f45375a40000000a --binary-syntax --close-stderr' exited with non-zero exit status 1: No protocol specified\nNo protocol specified\nAutolaunch error: X11 initialization failed.\n
```

I have tried a variety of settings for DISPLAY like export DISPLAY=ralph-Latitude-D610:0.0, but can't get things to work.

Any help appreciated.

---

### Post by LewisTM on 2012-09-17
Commands like [FONT="Courier New"]export[/FONT] and [FONT="Courier New"]&&[/FONT] are shell commands.
Do you have lines like this in your anacrontab?
> SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
This command should remove the need for shell interpretation
```
env DISPLAY=:0.0 /home/ralph/lbtest
```

Cheers!

---

### Post by steeldriver on 2012-09-19
Just wanted to follow up and report that this worked for me - ymmv

```

sudo -i
touch ~/.Xauthority
chmod 600 ~/.Xauthority
xauth -f ~/.Xauthority add $(xauth list "$DISPLAY")

```This creates a .Xauthority for root (didn't have a preexisting one because root has never started X on this box) and copies the MIT magic cookie from the current X session owner's .Xauthority to it

Then in the loggertest script, add

```
export DISPLAY=:0
export XAUTHORITY=/root/.Xauthority

```My /etc/anacrontab doesn't mention the display at all since it's set in the script

```
1    2    loggertest9    /home/steeldriver/bin/loggertest9
```Obviously this will only work for one user (and until the cookie changes) - I guess you could run the xauth add within the script to add the current cookie regardless of who owns :0 (and clean up by deleting on it exit).

Hope this helps

---

### Post by Ralph L on 2012-09-22
First, I want to thank everybody for the help.  I have been slow getting back to you, because I have been busy with other things.

Second, still no joy.  I can't get things to work.  Here are the particulars:

Current test script:  Note the debug statements.
```
#! /bin/bash

logger loggertest
export DISPLAY=:0

# Debug: Record the Xauthority setting for both root and ralph, before issuing the "export XAUTHORITY" command.
xauth -f /root/.Xauthority list
xauth -f /home/ralph/.Xauthority list

export XAUTHORITY=/root/.Xauthority/
echo "exports have taken place"

# Debug: Record the Xauthority settings for both root and ralph, after issuing the "export XAUTHORITY" command.
xauth -f /root/.Xauthority list
xauth -f /home/ralph/.Xauthority list

echo "Reached zenity command"
zenity --question --text "loggertest click yes or no"
# If the person said cancel, then tell them. If they said ok, then tell them that.
if [ "$?" == "1" ] ; then
    echo "You clicked cancel."
    exit
fi
if [ "$?" == "0" ] ; then
    echo "You clicked OK."
    exit

else echo "Input was neither a 0 nor a 1.  Something is wrong."
exit
```

Anacron calling line:
```
1	1	loggertest42	/home/ralph/loggertest1
```

Output from execution by Anacron (mailed to user root by sendmail)
```
Date: Fri, 21 Sep 2012 22:48:41 -0700
Message-Id: <201209220548.q8M5mfnh001914@ralph-Latitude-D610.local>
From: Anacron <root@ralph-Latitude-D610.local>
To: root@ralph-Latitude-D610.local
Subject: Anacron job 'loggertest43' on ralph-Latitude-D610

ralph-Latitude-D610/unix:0  MIT-MAGIC-COOKIE-1  ff0e4994582906e51c0d41ccaefa65a2
ralph-Latitude-D610/unix:0  MIT-MAGIC-COOKIE-1  663f17b555e6d6c26eeee1973479814b
exports have taken place
ralph-Latitude-D610/unix:0  MIT-MAGIC-COOKIE-1  ff0e4994582906e51c0d41ccaefa65a2
ralph-Latitude-D610/unix:0  MIT-MAGIC-COOKIE-1  663f17b555e6d6c26eeee1973479814b
Reached zenity command
No protocol specified
No protocol specified

(zenity:1911): Gtk-WARNING **: cannot open display: :0
```

See the various outputs from "xauth list".  They show that the magic cookie was not changed at all by the "export XAUTHORITY=/root/.Xauthority/" command in the script.  Since I don't know how Xauthority works, I am not sure whether this is ok or not.

Also, please note that the script was run by anacron immediately after a reboot.  I entered no commands before this ran.  I am not sure whether or not I should have run the 
"xauth -f ~/.Xauthority add $(xauth list "$DISPLAY")" command before the script was run (afer the reboot).  Of course I can't run any commands before the script runs, since the whole purpose of anacron is to run missed scripts immediately at startup.  Moreover, I think the "xauth -f ~/.Xauthority add $(xauth list "$DISPLAY")" command needs to be run under "user ralph" (the admin user), and I think the anacron script is being run under "user root".  I don't know how to run an anacron script under "user ralph".

---

### Post by spjackson on 2012-09-22
A couple of thoughts...

If this runs at system startup, doesn't anacron get started before X? Even if it doesn't it will run before the user has logged in, won't it? Is it supposed to work when nobody is logged in?

If it is only to run when someone is logged in, then instead of fiddling with xauth, can't you just do this?
```

su username -c 'zenity --question --text "loggertest click yes or no"'

```

---

### Post by Ralph L on 2012-09-22
spjackson

Yes!! The su command worked in the test script!!!  Thank you very much.  I put the su command you gave right after the "export DISPLAY=:0" command in the script.  I just had anacron call the script and everything ran.  I set the anacron wait time to several minutes so that I gave the user sufficient time to login.  I don't know what would happen if the script ran before the user logged in.   

Now I just need to get the real script installed.  That may take a few days, since I am busy.

If anybody knows why using xauth didn't work, I would appreciate an explanation.  I was completely unfamiliar with xauth before now, and I would like to know more about it and the whole theory for how Xauthority works.  I am trying to learn as much as I can for future ubuntu adventures.

Again, thanks to everybody for responding and helping me.

---

### Post by Ralph L on 2012-12-01
Just a final note on using anacron.  I decided that fcron/fcronq was a better scheduling system so I am using that.  See [http://ubuntuforums.org/showthread.php?t=2057486](http://ubuntuforums.org/showthread.php?t=2057486)

---

