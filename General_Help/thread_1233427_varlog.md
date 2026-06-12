---
title: "/var/log/"
date: 2009-08-06
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2009-08-06
what files can be deleted in there 
im trying to help my mom and it has 5.6GB
mine has less than 8MB
low disk space is the issue but do not want to up partition size
EDIT:
i got some file samples now this is around a day after the over-sized files were deleted
NOTE: replaced the username with user

---

### Post by TeoBigusGeekus on 2009-08-06
Try bleachbit
[http://bleachbit-project.appspot.com/]("http://bleachbit-project.appspot.com/")

---

### Post by pqwoerituytrueiwoq on 2009-08-06
she does not have the disk space to save a screen shot
much less download and install

---

### Post by TeoBigusGeekus on 2009-08-06
Have you tried uninstalling software you don't use any more?

---

### Post by Lampi on 2009-08-06
clear the apt package cache might be another idea:

```
sudo apt-get clean
```

---

### Post by pqwoerituytrueiwoq on 2009-08-06
> **TeoBigusGeekus said:**
> Have you tried uninstalling software you don't use any more?
the only programs other than the default one are thunderbird and firefox 3.5.2 and mail-alerts, bleach bit (used the above command line to get space)
ubuntu is installed to an 8.some gb partition
no music, no videos, a few kb of documents
/var/log/ has over 5gb of stuff
dual boot with vista

---

### Post by mcduck on 2009-08-06
The log files are automatically removed over time, and their size definitely shouldn't grow to gigabytes.

If logs are that large, that's pretty much a sign that there's some problem on that system which floods some log file with error messages. You really should check which log is that big, and check what errors there are & solve the problem. Removing log files won't give you any real help, unless you fix the actual problem the logs will soon grow back to the same size..

To quickly free some disk space do what Lampi suggested and clean your packages cache.

---

### Post by pqwoerituytrueiwoq on 2009-08-06
this happend before i reinstalled ubuntu
now it happend again
it has not even been a week yet

---

### Post by dcstar on 2009-08-07
> **pqwoerituytrueiwoq said:**
> this happend before i reinstalled ubuntu
now it happend again
it has not even been a week yet

Then actually look at the log files and find out **what is causing the problem** that is filling them up.

Ignoring the problem is not going to prevent it happening again.

---

### Post by pqwoerituytrueiwoq on 2009-08-09
The files were:
kern.log - 832.3 MB
Messages - 832.3 MB
syslog - 2.0 GB
user.log - 1.8 GB
files were too big do display

---

### Post by Barafu Albino Cheetah on 2009-08-09
The guy seem to have some hardware error that makes the kernel to scream for help.

---

### Post by adempewolff on 2009-08-09
The files are probably that big because the same error is happening again and again and again.  Even if the entire files are obviously too big to display, open them look for the error message(s) that are likely just repeated 10,000 times and paste one instance of the error message(s) here.  I'm sure someone could then help you out or at least point your in the right direction.

---

### Post by pqwoerituytrueiwoq on 2009-08-09
uploaded some file samples into 1st post
had no idea of what to look for

---

### Post by mcduck on 2009-08-10
I didn't notice anything interesting in those files, but they seem to be from the very top of the log files, and only contain startup messages. The errors most likely start happening at later stage.

Next time you notice that the log files start growing you could use the following commands to catch a part from the end of the log files:

```
tail -n 100 /var/log/syslog > ~/Desktop/syslog.txt
tail -n 100 /var/log/user.log > ~/Desktop/userlog.txt
```

(These commands read 100 last lines from the log files and save them into text files on your desktop)

---

