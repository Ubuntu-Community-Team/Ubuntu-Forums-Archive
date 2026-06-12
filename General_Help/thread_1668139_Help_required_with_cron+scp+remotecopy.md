---
title: "Help required with cron+scp+remotecopy"
date: 2011-01-15
forum: General Help
---

### Post by andygmorris on 2011-01-15
I've trawled many posts over the last few days and tried everything that I think will help me solve this issue, but I still can't figure it out.

Here's the problem :-

I have a script that works fine when run from the command prompt, but when it's run from a cron job, the 'scp' command doesn't perform the remote copy.

There is a twist. To test the scp command is actually being run, I changed the action from a remote copy to a local copy just to see if I can copy one local file to another. And, yes, that works perfectly fine.

So it's something to do with scp + remote copy + cron, as I can clearly see that the cron is being actioned, the script is being called, and the scp command is running ... working with local files, but not with remote files.

My local pc is trusted by the server, so when I run the scp manually, I'm not prompted for a server password.

The crontab is set with :-
   SHELL=/bin/sh
   PATH=/sbin:/bin:/usr/sbin:/usr/bin
   +thecronjob

Does anyone have any suggestions, that will identify configuration settings that will cause 'scp' not to work correctly with remote files when being run in cron!

Here's hoping that someone's already found a fix for this one, as it's driving me nuts!

--------------
Running ubuntu 10.04 LTS, fully updated.

---

### Post by bodhi.zazen on 2011-01-15
Post the script =)

Or at least the scp command, my guess is that cron is working and scp is awaiting a password or if you are using a key perhaps the syntax of your scp command is off.

---

### Post by andygmorris on 2011-01-15
> **bodhi.zazen said:**
> Post the script

Thanks for replying.

details masked for privacy, so I hope it's enough info...

#
echo "running..." >> /home/andy/Scripts/result3.txt
#
scp -r {user}@{server_ip}:{path}/myfile.tar.gz /home/andy/Scripts/myfile.tar.gz
#
echo "finished..." >> /home/andy/Scripts/result3.txt
#

When this runs, 'running' and 'finished' is appended to 'results3.txt', however, no file is copied.

Run the same script outside of cron (with the first line of "#!/bin/bash") and the script is running fine.

Inside cron, if I use 'scp -v' I get no information.
Outside of cron, -v option shows me plenty (but I wouldn't be able to post that openly due to security issues).

Does any of this help you at all?

---

### Post by efflandt on 2011-01-16
If you want to see why it is not working in cron, why don't you send stdout and stderr of the scp command to a file.  I forget if the 2>&1 goes before or after the file redirection, but in this case I don't think it matters (all on one line):

scp -r {user}@{server_ip}:{path}/myfile.tar.gz /home/andy/Scripts/myfile.tar.gz 2>&1 >> /home/andy/Scripts/result3.txt

Or try that initially with -v instead of -r (not sure why you are using -r unless you eventually intend to copy directories and subdirectories, instead of just a file).

---

### Post by andygmorris on 2011-01-16
> **efflandt said:**
> scp -r {user}@{server_ip}:{path}/myfile.tar.gz /home/andy/Scripts/myfile.tar.gz 2>&1 >> /home/andy/Scripts/result3.txt

Ok thanks. I'll give that a go and see if it identifies any more information.

The -r is used as files+subdirs would be copied later. In this example we're looking at, you're right to say it's not relevant here.

---

### Post by bodhi.zazen on 2011-01-16
How are you entering the password for scp ?

---

