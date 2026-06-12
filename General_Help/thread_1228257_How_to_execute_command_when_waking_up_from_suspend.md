---
title: "How to execute command when waking up from suspend?"
date: 2009-07-31
forum: General Help
---

### Post by andresmh on 2009-07-31
There is a bug that prevents my built-in broadband modem on my laptop wake up from suspend mode. I [reported it]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405053") already and I found that a temporary solution is to execute 'rfkill unblock wwan'  after waking up.

I would like this command to be automatically executed after waking up.

Based on [this threadI]("http://ubuntuforums.org/showthread.php?t=472830") tried creating a script but it doesn't seem to be executed:

```

$ ls -la /etc/acpi/resume.d/90-wwan.sh 
-rwxr-xr-x 1 root root 34 2009-07-31 10:53 /etc/acpi/resume.d/90-wwan.sh
$ cat /etc/acpi/resume.d/90-wwan.sh 
#! /bin/sh
rfkill unblock wwan

```

Does anyone know how I could do this?

---

### Post by kilowattradio on 2009-07-31
> **andresmh said:**
> There is a bug that prevents my built-in broadband modem on my laptop wake up from suspend mode. I [reported it]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/405053") already and I found that a temporary solution is to execute 'rfkill unblock wwan'  after waking up.

I would like this command to be automatically executed after waking up.

Based on [this threadI]("http://ubuntuforums.org/showthread.php?t=472830") tried creating a script but it doesn't seem to be executed:

```

$ ls -la /etc/acpi/resume.d/90-wwan.sh 
-rwxr-xr-x 1 root root 34 2009-07-31 10:53 /etc/acpi/resume.d/90-wwan.sh
$ cat /etc/acpi/resume.d/90-wwan.sh 
#! /bin/sh
rfkill unblock wwan

```

Does anyone know how I could do this?

Is #! /bin/sh a misprint on this web page or is there a space there in the file 90-wwan.sh ? if there is a space that would be the thing to fix and see if that is the problem.

Also you should put the full path to rfkill.

---

### Post by wojox on 2009-07-31
Try this:

```
#!/bin/bash
echo password | sudo -S rfkill unblock wwan
```

Replace password with your sudo password.

---

### Post by andresmh on 2009-07-31
> **wojox said:**
> Try this:

```
#!/bin/bash
echo password | sudo -S rfkill unblock wwan
```

Replace password with your sudo password.


I tried that, suspended, woke up and the wwan didn't wake up. I then executed the script manually and it woke the wwan up. So then I thought that maybe the script was not being called upon waking up, so I added a touch /tmp/foo line at the end of the script and I could confirm that the /tmp/foo was created after waking up. So it seems like there's something wrong with the script? :(

---

