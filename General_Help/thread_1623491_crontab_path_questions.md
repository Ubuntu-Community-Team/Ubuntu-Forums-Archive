---
title: "crontab path questions"
date: 2010-11-16
forum: General Help
---

### Post by Cool Javelin on 2010-11-16
Can I change the default path for any or all of the different crontab files?

Can they be changed independently? for example can the user mark get one path for cron jobs, Lynn get another, and root get yet a third, or are they always going to be the same?

How do I change them?

Hello fellow Linux users:

I know there are several crontab files on my computer. One each for each user, and it looks like one for root, maybe others?

I think there is only one cron handler that reads all the different crontab files and does what it is told.

If I do from my command line, I get:```
mark@server:~$echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```

If I schedule a similar command in my own crontab file by using ```
mark@server:~$crontab -e
``` with the following line:
```
* * * * * echo $PATH > /home/cronpath
```
then:
```
mark@server:~$cat /home/cronpath
/usr/bin:/bin
```

And further if I use sudo```
mark@server:~$sudo crontab -e
```I seem to get a different crontab file, and insert the following line:
```
* * * * * echo $PATH > /home/rootcronpath
```
then I get the similar output:
```
mark@server:~$cat /home/rootcronpath/usr/bin:/bin
```

Thanks, Mark.

---

### Post by efflandt on 2010-11-16
You should not assume anything in the environment for anything you do from crontab.  You should either use full paths, or specifically set any desired environment in your crontab or export any desired variables from a script run from cron.

In a terminal see: **man 5 crontab**

Remember that a shebang (first) line of shell script **#!/bin/sh** now uses **dash** instead of bash.  So if you specifically need something that **bash** does, you should use **#!/bin/bash**

---

### Post by cinohpa on 2010-11-16
The short answer to your first 2 questions is yes.

The short answer to your third question is play around with it. You can only break your computer. :p Make back ups!

Also just explicitly try reading /etc/crontab. You will see how they set up the environment there and how it configures your various cron scripts. 

If you are still curious read some of the scripts in /etc/cron.hourly|daily|weekly and see how they work.

It helps to have examples to understand how cron works.

---

