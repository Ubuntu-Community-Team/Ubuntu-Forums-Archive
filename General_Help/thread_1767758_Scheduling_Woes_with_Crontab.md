---
title: "Scheduling Woes with Crontab"
date: 2011-05-26
forum: General Help
---

### Post by Kissell on 2011-05-26
I have a python script I can run from the command line, "tvnamer -c /usr/bin/tvnamer.cfg -r -b /media/DATA/Uploads/Television".  It works great, from any folder, but I am putting the same command into the crontab, but it is not working at all.  Please help.

I run "crontab -e" as root and then put in this command.

> 
0 * * * * tvnamer -c /usr/bin/tvnamer.cfg -r -b /media/DATA/Uploads/Television


Then I hit CTRL-X and save.  

The idea, would be it would run that command every hour, but several hours have passed and it isn't working.

NOTE: -c parameter loads a config file, -r is recurrsive, -b is batch (unattended mode).   The same command works perfectly if run manually.

---

### Post by Grenage on 2011-05-26
Use the full path to the file *tvnamer*, that should work; example:

```
0 * * * * /usr/bin/tvnamer -c /usr/bin/tvnamer.cfg -r -b /media/DATA/Uploads/Television
```

---

### Post by Kissell on 2011-05-26
Dup

---

### Post by Kissell on 2011-05-26
> **Grenage said:**
> Use the full path to the file *tvnamer*, that should work; example:

```
0 * * * * /usr/bin/tvnamer -c /usr/bin/tvnamer.cfg -r -b /media/DATA/Uploads/Television
```

EDIT: Ok, I found it's location using > find ./ |grep tvnamer it was in /usr/local/bin instead of /usr/bin.

Added the full path and it works!  Yeah!

---

### Post by Grenage on 2011-05-26
> **Kissell said:**
> I cheated to install "tvnamer" by using "easy_install" so I don't know where the path is...  it isn't in /usr/bin...  what is an easy way to find it's location?

```
which tvnamer
```

Give that a whirl!

EDIT:

Your second test may not work due to the "~" shortcut, I've never used them in cron, so I have no idea if it would actually resolve them.

---

### Post by Kissell on 2011-05-26
It did start working once I had the full path...  cool.

I expected it to work without the path, because it does from the command line...  evidentally /usr/bin is in the path, but /usr/local/bin is not, unless being run locally?

---

### Post by Grenage on 2011-05-26
> **Kissell said:**
> It did start working once I had the full path...  cool.

I expected it to work without the path, because it does from the command line...  evidentally /usr/bin is in the path, but /usr/local/bin is not, unless being run locally?

I believe that the path variables can be modified, have a look at the output:

```
cat /etc/crontab
```

I always specify full paths, it's just easier for me to stay in the habit.

---

### Post by Kissell on 2011-05-26
Huh, /usr/local/bin is in the path

> cat /etc/crontab
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin


oh well, it is working now.

I normally do the full path too, just didn't know where this one was located.

---

