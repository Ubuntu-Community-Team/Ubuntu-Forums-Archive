---
title: "Monitor for a process (not-running yet) and see who it is running as"
date: 2012-05-01
forum: General Help
---

### Post by chriv on 2012-05-01
This is more of a general linux question, but it applies to an Ubuntu Server running 12.04 (in this case).  **If you are impatient, skip to the big, bold, red text below for the direct question.**

I'm having a problem with permissions for png files being served by apache.  The files are being created by the program /usr/bin/dot, but they are zero bytes, which implies to me that the user running /usr/bin/dot doesn't have proper permissions to write to the files.

Here's the problem. /usr/bin/dot is being run by bugzilla for a fraction of a second.  I don't know what user it is running /usr/bin/dot as.  Without knowing that, I cannot fix the permissions for the directory or add permissions to the user.

**[SIZE="4"][COLOR="Red"]How do I monitor for a process that isn't running, and log the details about the process once it does run (especically the user and group it is running as)?[/COLOR][/SIZE]**

---

### Post by chriv on 2012-05-01
I might have figure out a way:

I wrote a small bash script and named it /usr/bin/mydot and gave it permissions 766:
```
#!/bin/bash
echo "/usr/bin/dot run as $(whoami)" 1>>/tmp/dotrun.log 2>>dotrun.err
/usr/bin/dot $*
```

I then ran:
```
cd /tmp
touch dotrun.log
touch dotrun.err
chmod 666 dotrun.log
chmod 666 dotrun.err
```

I then configured bugzilla to run /usr/bin/mydot instead of /usr/bin/dot.

I ran:
```
sudo -u ftp mydot test
```

It logged:
```
/usr/bin/dot run as ftp
```

I then tried to get bugzilla to run "mydot", and my log now looks like this:
```
/usr/bin/dot run as ftp
/usr/bin/dot run as
/usr/bin/dot run as
```

Notice the last two lines don't show the user, so it didn't work.

Anybody got a better way?

---

### Post by chriv on 2012-05-01
I got it to work.  I had to explicitly give the full path of whoami to get it to work.  I got a little aggressive with my script, so here is what /usr/bin/mydot looks like now:
```
#!/bin/bash
echo "/usr/bin/dot run as $(/usr/bin/whoami) according to whoami" 1>> /tmp/dotrun.log 2>> /tmp/dotrun.err
echo "/usr/bin/dot run as $(/usr/bin/id -u -n) according to id -u -n" 1>> /tmp/dotrun.log 2>> /tmp/dotrun.err
echo "/usr/bin/dot run as $USER according to environment variable" 1>> /tmp/dotrun.log 2>> /tmp/dotrun.err
/usr/bin/dot $*
```

whoami and id -u -n worked.  The USER environment variable did not.

---

### Post by chriv on 2012-05-01
P.S. It turns out the actual problem was a bad distro version of graphviz.  I compiled graphviz from scratch and dot worked perfectly. :)

If anyone knows of a way to monitor for a process that isn't running (and log it when it does), I would appreciate knowing what it is.

My workaround script is kind of a hack, but it did allow me to find out who the user running dot was. ;)

---

