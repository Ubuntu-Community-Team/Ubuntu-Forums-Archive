---
title: "running shell script cl vs cron"
date: 2010-02-27
forum: General Help
---

### Post by tdg911 on 2010-02-27
I have recently made the switch from FreeBSD to Ubuntu and have run across this scenario a few times and cannot remember the fix to save my life.

Currently running: Ubuntu-Server-9.10 x86
Kernel: 2.6.31-14-generic-pae

For example in one of my scripts I am building a list of files in a directory to run thru a loop.
in building the list I basically use this syntax:

FILES=`ls -al $INDIR | egrep -v "(^d|omit_files1" | awk '{print $8}'` this will print out the filename just fine.

When run via cron the output looks like the the 7th column is being printed out instead of the 8th like i have it written in the script.

I vaguely remember something about the LANG variable being the culprit, which is en-US.UTF-8

Crons env:
HOME=/root
LOGNAME=root
PATH=/usr/bin:/bin
SHELL=/bin/sh
PWD=/root

Any suggestions or ideas?  

Thanks in advance

---

### Post by DaithiF on 2010-02-27
yes i think it is a locale setting that influences this.  rather than battling this, why not just drop the 'l' from your ls, if all you want is the filename anyway then no need to use the longform output

---

### Post by tdg911 on 2010-02-27
> **DaithiF said:**
> yes i think it is a locale setting that influences this.  rather than battling this, why not just drop the 'l' from your ls, if all you want is the filename anyway then no need to use the longform output

Habit I guess with the long format.  I also do a few checks based on date and/or filesize. albeit this may correct my file list now but I'm going to run into these issues in the future for sure.  I have several other servers that initially had this problem but like I mentioned in my original post, i just can't seem to recall what was done.

Very frustrating to say the least.  3.5hrs on a darn cron/shell/env issue.  /sigh

Thanks

---

