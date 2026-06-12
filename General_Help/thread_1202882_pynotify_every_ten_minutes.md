---
title: "pynotify every ten minutes"
date: 2009-07-02
forum: General Help
---

### Post by dranorter on 2009-07-02
Short version: How do I automate a libnotify notification occurring every ten minutes? Or what might be better for this than libnotify/pynotify?

I am trying to build a random notification program. The idea will be to randomly show information from a text file every ten minutes; quotes, to-do items, perhaps Twitter updates dumped into a file. Right now I have the following code, which displays a fortune.

```
#!/usr/bin/env python

import os
import pynotify

pynotify.init("random information")
s = os.popen("fortune -n 100 -s","r").read()
n = pynotify.Notification("Fortune",s)
n.show()
```

However, when I tried to run this every ten minutes with cron, it didn't show, even though I was able to successfully run it as root. (I tried the root crontab and my user crontab...) So I'm thinking it doesn't get access to my X instance, or perhaps the running notifier daemon, or whatever libnotify needs, when it's run by cron.

Anyone know how I could get this simple script to run every ten minutes? 

Additionally: Ultimately, when this actually notifies me of useful things rather than just silly quotes, I'll want to be able to attach notifications to arbitrary bash commands or executables. I would want to click on them to launch some behaviour. What could I use to accomplish that? I've found something called mumbles but don't know if it has that feature yet; notify-osd (called by pynotify unless interactions are added to the notification) doesn't. Is there another, featureful notification option?

---

### Post by Endolith on 2009-07-21
Scratch what I wrote.  I didn't realize your script actually works.  :)

libnotify uses dbus, and I hear cron has trouble talking to dbus.  You have to get the right dbus instance first or something.

[http://ubuntuforums.org/showthread.php?t=615882](http://ubuntuforums.org/showthread.php?t=615882)

Also, could you just use time.sleep(10*60) and put a loop in your script?

What do you mean by "attach notifications to commands"?

---

### Post by LightningCrash on 2009-07-21
Why not have python run the loop every 10 minutes?

---

### Post by t4thfavor on 2009-07-21
Maybe you want to daemonize this script, and make it run persistently. You can have interrupts, and catch system signals. Ultimately it may be more flexible.


There are lots of tutorials available. 

I wrote a similar notification daemon for asterisk in perl, and it wasn't very hard at all.

---

### Post by Endolith on 2009-07-21
This might be a solution:

[http://www.chicagolug.org/pipermail/chicagolinux-discuss/2007-July/000734.html](http://www.chicagolug.org/pipermail/chicagolinux-discuss/2007-July/000734.html)

>  "Gnome Schedule does not support yet setting environment variables for recurrent tasks, but it will do soon. In the meantime, you can manually create a script that first defines DISPLAY variable and then calls the graphical application. Finally, you can create a recurrent task to launch the script."



---

### Post by Endolith on 2009-07-21
**This** worked for me:

[http://wwwjfy.blogspot.com/2009/03/problem-when-using-pygtk-with-crontab.html](http://wwwjfy.blogspot.com/2009/03/problem-when-using-pygtk-with-crontab.html)

```
40 22 * * 1-5 env DISPLAY=:0.0 /home/endolith/Applications/bedtime.py #JOB_ID_2

```Whyyyyy must Linux be so difficult?

---

### Post by LightningCrash on 2009-10-31
> **Endolith said:**
> **This** worked for me:

[http://wwwjfy.blogspot.com/2009/03/problem-when-using-pygtk-with-crontab.html](http://wwwjfy.blogspot.com/2009/03/problem-when-using-pygtk-with-crontab.html)

```
40 22 * * 1-5 env DISPLAY=:0.0 /home/endolith/Applications/bedtime.py #JOB_ID_2

```Whyyyyy must Linux be so difficult?

Well, that's really more because of X and not Linux. Since there can be multiple X servers running on a machine, it can't automatically assume which one you intended. Think of it like running a Scheduled Task on a Windows Terminal Server.

---

