---
title: "Running a command on startup and out of hibernate"
date: 2011-04-04
forum: General Help
---

### Post by unboogyman on 2011-04-04
Hi, my computer has a hard drive clicking problem that is easily fixed by using:
```
sudo hdparm [COLOR=#660033]-B[/COLOR] [COLOR=#000000]254[/COLOR] [COLOR=#000000]**/**[/COLOR]dev[COLOR=#000000]**/**[/COLOR]sda
```The only problem is that I have to do it every time I boot or come out of sleep/hibernate.

Is there a way I can automate that command?  I'm a linux noob so please explain in easy steps.

Thanks.

---

### Post by mikewhatever on 2011-04-04
I think you just need to add the command to /etc/rc.local, so that it looks like thins:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
hdparm -B 254 /dev/sda
exit 0

```

To open the file for editing use the following command:
```
gksudo gedit /etc/rc.local
```

---

### Post by Learning Linux 2011 on 2011-04-04
Clicking usually means impending failure.

---

### Post by unboogyman on 2011-04-04
> **Learning Linux 2011 said:**
> Clicking usually means impending failure.
Not in this case, I looked it up and is common in my laptop model (EeePC 1215T).  A lot of people had clicking and it runs fine.

The command I used gets rid of the click completely.

---

