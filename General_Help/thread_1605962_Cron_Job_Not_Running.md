---
title: "Cron Job Not Running?"
date: 2010-10-25
forum: General Help
---

### Post by csharpplus on 2010-10-25
Cron refuses to work for a newbie. Any chance you guys can help?

I am trying to setup a cron job to backup a folder in my home directory ('/home/scratch') to a folder ('home/internet_backup') that is mounted (using nfs) to a network folder.

the folder ('home/internet_backup') is mounted correctly to the network folder upon system startup, so this part works.

I created a simple bash file (rsync-shell.1.sh) that looks like this:

```

# backup the contents of 'scratch' (of 'internet' machine) into '/home/aa/internet_backup/'
# the latter folder ('/home/aa/internet_backup/') is mounted to 'developer' machine
rsync -av --exclude=".*" /home/aa/scratch /home/aa/internet_backup/
#

```when manually running this bash file from my home directory (./rsync-shell.1.sh) everything works, and the contents are written to the destination folder.

Yet, instead of running this manually, I wanted this to be executed by Cron every 30 min. so I first chmod +x this file, and then copied it (using sudo) to /root.

I then created the following using 'sudo crontab -e':

```

# m h  dom mon dow   command
10       *       *       *       *       /root/rsync-shell.1.sh

``` This is the same bash file illustrated above, yet, it doesn't work (files are not being written to the destination folder).

What am I missing here?  thanks in advance for any help.

---

### Post by efflandt on 2010-10-26
You cannot assume PATH for anything run from cron (or anything else in the environment), so you should use full paths for binaries (programs) like /usr/bin/rsync

Unless aa is root, do you really want to run the cron job as root?  Then aa would not be able to do anything with files written to the destination without using sudo.  Or are those directories/files owned by root anyway?

Your script is missing a shebang line on 1st line to specify what shell to use like:
#!/bin/bash
or
#!/bin/sh (**dash** shell which does some things different than bash)

---

### Post by DaithiF on 2010-10-26
Hi, 
A couple of points:
1. Why are you running it under roots crontab rather than your own?  If it runs ok from the command line under your user name then run it under your own cron.
2. You may be experiencing the problem described here: [http://ubuntuforums.org/showthread.php?t=1267248](http://ubuntuforums.org/showthread.php?t=1267248)
try the solution in my post on that thread, ie. adding 
MAILTO=""
to the top of your crontab.

---

### Post by k999 on 2010-10-26
A nice way to debug cron jobs is to add this to your crontab:

* * * * * /bin/date > /tmp/crontest

Then you can watch for the /tmp/crontest file to see if it runs, it should be updated every minute. Doesn't get much simpler than this. Don't forget to disable it later.

---

### Post by csharpplus on 2010-10-26
Thanks guys -- your advice helped and this is now solved!

---

