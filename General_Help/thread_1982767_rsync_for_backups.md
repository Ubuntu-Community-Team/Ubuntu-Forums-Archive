---
title: "rsync for backups"
date: 2012-05-19
forum: General Help
---

### Post by ryanyeah on 2012-05-19
What are the best options to use with rsync? I am planning on using rsync as a primary backup process and am not sure if a simple rsync with -r (recursive) between directories will be enough or whether I should add other arguments.

---

### Post by bruno9779 on 2012-05-19
I really like Grsync, gnome's graphic frontend to rsync.

It is very easy to use and most command line options can be enabled ticking a box. You can save your settings if you need to run it more than once (eg. my pics to my external HDD once a month)

---

### Post by habana on 2012-05-19
I had a similar question which involved symlinks in my case. See this thread for the advice I was given:
[PHP][/PHP][http://ubuntuforums.org/showthread.php?t=1980796](http://ubuntuforums.org/showthread.php?t=1980796)
See the rsync man page for a detailed description of the various arguments but note the definition of a file system is not what might expect.

Good luck!

---

### Post by papibe on 2012-05-19
Hi ryanyeah.

The most common command is like this:
```
rsync -av  source/  destination
```
where:
[INDENT]-a and -v are rsync options.

-a is like a macro (several options including -r). It preserves time, ownership, and can be use to copy whole directories, not just a file.

-v means verbose so it will display what it's doing. Its benefit will be more obvious when you are transferring several files.
[/INDENT]
Hope that helps.
Regards.

---

### Post by markbl on 2012-05-20
For backups, I have used rsnapshot for years. It is in the standard packages. It uses rsync under its hood but creates daily, weekly, monthly etc "snapshots". It uses file links so does not use much extra space for each snapshot. I install deltacopy (windows rsync server) on my wife windows pc and so rsnapshot (i.e. rsync) pulls backup copies from there also.

---

### Post by chocklet on 2012-05-20
> **ryanyeah said:**
> What are the best options to use with rsync? 

If you have done any googling about rsync, then you are understandably... confused.

Much of the advice about rsync options on the web seems to conflict, or at least doesn't make sense.  Here are some of the suggestions for how you might backup your home directory:

rsync -avt

rsync -arvu

rsync -arvuz

rsync --progress

rsync -avP

rsync -azvu --log-file=/var/log/waynodaily.log --append
--exclude '.gvfs'

(the above examples are copy and pasted from various articles on rsync)

The "a" option is described by the man page as follows...
-a, --archive               archive mode; equals -rlptgoD (no -H,-A,-X)

In other words, "a" includes "t", and "r", so the first three examples above appear to include redundant options.

The fourth example includes only the "--progress" option.  Not "a".  This is the only guy who leave out "a".  I have no idea why.

The "P" in the 5th example is described as follows...
-P  same as --partial --progress

#1,#2,& #3 advise "a" but not "-P".
#4 advises "--progress" but not "a".
#5 advises "a" and "P".
So, with regard to "a" and "P" (--progress), the typical noob, like me, really is left with more questions than answers.

The man page has this note...
To backup my wife's home directory, which consists  of  large  MS  Word files and mail folders, I use a cron job that runs

              rsync -Cavz . arvidsjaur:backup

Yep, the author of the man pages, and he alone, advises "C".  "C" means...
-C, --cvs-exclude           auto-ignore files in the same way CVS does

In the man pages there is lots of verbiage about "cvs", but just in case you don't get totally lost there is also the recommendation that you...
"See the cvs(1) manual for more information."

Bottom line... a noob has no chance in hell to figure out just what options he should use for rsync.  He has to take someone's advise on faith, and figure the others have it wrong.

Before experimenting it is normal to caution a noob to backup everything first... that's right, before experimenting your first job is to figure out all this stuff.

Good Luck!

PS  I'm thinking about going with "-Cavz" options, because the guy says he uses it to back up his wife's directory, so he better have it right or he'll end up sleeping on the couch!  Yep, my money is on that guy!

---

### Post by kurt18947 on 2012-05-20
> **bruno9779 said:**
> I really like Grsync, gnome's graphic frontend to rsync.

It is very easy to use and most command line options can be enabled ticking a box. You can save your settings if you need to run it more than once (eg. my pics to my external HDD once a month)

I agree.  Grsync is pretty straight forward for non-expert desktop users.  It doesn't support synchronization directly but I've created two sessions.  One session copies files in A to B.  The second session copies files from B to A.  The end result seems to be two directories containing the latest version of the same files. 

If synchronizing is the goal, there's a java app that works similar to different Windows utilities and only requires Java so it works on any machine that has Java installed.  

[http://www.dirsyncpro.org/](http://www.dirsyncpro.org/)

---

### Post by Dave_L on 2012-05-20
I use these options:

--archive (equivalent to -a)
--delete
--verbose (equivalent to -v)
--stats

---

