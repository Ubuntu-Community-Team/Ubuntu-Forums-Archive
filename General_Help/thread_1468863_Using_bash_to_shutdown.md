---
title: "Using bash to shutdown"
date: 2010-05-01
forum: General Help
---

### Post by Millnert on 2010-05-01
Hi, quick question, I would like to make a bash script that shuts down. Problem is... How am I supposed to do this when shutdown requires sudo and ultimately requiring me enter my password as a response?
I.e.
#/bin/bash
#Do: shutdown at xx : xx time
shutdown 23:45
#done (yea just one line...)

How could I make sure my password is given to the sudo response without manually entering it ever time?

Another thing... How could one make this script run automatically i.e. on startup every time.
Thanks, T.

---

### Post by robvas on 2010-05-01
> **Millnert said:**
> Hi, quick question, I would like to make a bash script that shuts down. Problem is... How am I supposed to do this when shutdown requires sudo and ultimately requiring me enter my password as a response?
I.e.
#/bin/bash
#Do: shutdown at xx : xx time
shutdown 23:45
#done (yea just one line...)

How could I make sure my password is given to the sudo response without manually entering it ever time?

Another thing... How could one make this script run automatically i.e. on startup every time.
Thanks, T.

Are you trying to shut the computer off at a certain time every day?

You can use the[FONT=Courier New] at [/FONT]command, or setup a [FONT=Courier New]cron[/FONT] job

For more information on those two options see this link: [http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html](http://www.cyberciti.biz/tips/howto-shutdown-linux-box-automatically.html)

---

### Post by vibra on 2010-05-01
Look at this previous thread and see if it helps you :)

[http://ubuntuforums.org/showthread.php?t=826935](http://ubuntuforums.org/showthread.php?t=826935)

---

