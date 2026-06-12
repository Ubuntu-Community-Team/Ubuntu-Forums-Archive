---
title: "Some crontabs run, others won't.  Don't know why."
date: 2009-12-25
forum: General Help
---

### Post by chip616 on 2009-12-25
I am trying to make a backup script run as a cron job.  I used kcron to set it up.  It failed to run.  I checked syslog, and it shows that it ran at the time specified.

To eliminate variables, I tried editing the crontab with crontab -e.  The following worked:

```
# Test
05 15 * * *     echo "this worked" > /home/frank/crontext.txt
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
```

The above did create a file called 'crontext.txt' in my home directory, and it did contain the words 'this worked'.

So, now I know that permissions and so on are not an issue.  Cron is working, and the above crontab DID run successfully.

However, I edited it a bit as follows, again to test what can be done:

```
# Test
10 15 * * *     digikam
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
```

This did NOT open digikam on my machine.  Syslog shows that the crotab ran.  However, nothing happened.

I also tried giving it the full path, as follows:

```
# Test
15 15 * * *     /usr/bin/digikam
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.
```

That did not work either.

Reading a tutorial here, it says that the default shell for cron is sh, not bash.  So I tried overriding that as follows:

```
# Test
SHELL=/bin/bash
40 15 * * *     /usr/bin/digikam
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.

```

No difference.

So, what's up?  Why do some commands work, and not others?  I'm stumped.

I've searched the forum, but I found nothing that applied to this issue.  FWIW, I'm running Kubuntu 8.04.

Frank.

---

### Post by falconindy on 2009-12-25
The environment that cron runs in is effectively blank. If you're trying to open an app with a GUI via cron, you'll need to specify **where** it needs to open. Try prepending the command with 'DISPLAY=:0.0' (sans quotes of course).

Also, get rid of the line forcing the shell. If you really want to change the effective shell for a program, use 'bash -c <command>'.

---

### Post by chip616 on 2009-12-25
falconindy:

> If you're trying to open an app with a GUI via cron, you'll need to specify where it needs to open. Try prepending the command with 'DISPLAY=:0.0' (sans quotes of course).

Well, that worked for the GUI, but I only tried that to try to REDUCE some variables.  What I really want to do is to run a shell script that uses a couple of rsync commands.  I've already set those scripts up with ssh and rsa keys so that they will run unattended, synchronizing data directories across several machines.  That script works fine when run from a console.  I can't make it work in crontab, however.

Here is what I actually want to run:

```
# SyncV-O
40 18 * * *     /home/frank/data/base/fdata/ShellScripts/syncV-O.sh
# This file was written by KCron. Copyright (c) 1999, Gary Meyer
# Although KCron supports most crontab formats, use care when editing.
# Note: Lines beginning with "#\" indicates a disabled task.

```

The script that it runs is:

```
#! /bin/bash

# Synchronizes Vostro laptop with Office machine.  Must run from Vostro.

echo
echo "Sending data to remote machine"
echo
rsync -avzu -e ssh /data/* frank@192.168.1.246:/hdb1/data
echo
echo "Receiving data from remote machine"
echo
rsync -avzu -e ssh frank@192.168.1.246:/hdb1/data/* /data
echo
echo "Done!"
echo
```

I assume that I have to prepend something here as well, like perhaps a console.  However, I'm not sure how to go about that.

Thanks for the help thus far.

Frank.

---

### Post by chip616 on 2009-12-25
Correction.  That does work now.  No idea why it wouldn't before.

Thanks.

Frank.

---

