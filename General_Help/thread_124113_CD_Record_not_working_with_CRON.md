---
title: "CD Record not working with CRON"
date: 2006-01-31
forum: General Help
---

### Post by matouka on 2006-01-31
Hi all,

I am left a little bewildered here. Each day I have the computer here backing up some databases and directories then burning them to CD using CDRecord. I have a computer running 'Hoary' and the script works perfectly. I recently setup a new computer and installed 'Breezy'. The same script that works perfectly with 'Hoary' fails to burn the CD with 'Breezy'.

I have trimmed the script down to isolate where I think it is going wrong. The really funny thing is that if I run the script, when logged in as root, it runs through without any trouble. The CRON job is assigned to the root user so I assume the permissions should be the same?

Here is the cron line:
```
35	9	*	*	1-6	sh -x /home/Backup/test.sh > /home/Backup/output.txt
```

Here is the script I am running (test.sh):
```
echo "STEP 1"
cd /home/Backup
echo "STEP 2"
chmod 777 /home/Backup/image.iso
rm /home/Backup/image.iso
echo "STEP 3"
mkisofs -J -o image.iso /home/burndir
echo "STEP 4"
chmod 777 /home/Backup/image.iso
echo "STEP 5"
cdrecord blank=all dev=ATAPI:0,0,0
echo "STEP 6"
cdrecord -v dev=ATAPI:0,0,0 /home/Backup/image.iso
echo "Complete"
```

After CRON executes this script I get the following output (output.txt):
```
STEP 1
STEP 2
STEP 3
STEP 4
STEP 5
```

Would anyone out there have any suggestions as to why this would work when logged in as root, but fail when the CRON job is run as root??

Regards,

Paul.

---

### Post by z_diver on 2006-01-31
I came across an issue like this last week and it had to do with one of the steps requiring X11 which cron can't run so the whole process broke down.  I don't see anything like that in your script but it's something to keep in mind.

---

### Post by dcstar on 2006-01-31
[QUOTE=matouka]
......
Would anyone out there have any suggestions as to why this would work when logged in as root, but fail when the CRON job is run as root??

Regards,

Paul.[/QUOTE]
Running in a terminal is running in a shell, with all the paths and environment stuff set up.

You do not seem to have a shell defined in your script, have a look at other scripts in /etc/init.d for examples of how they are structured.

---

### Post by matouka on 2006-01-31
[QUOTE=dcstar]Running in a terminal is running in a shell, with all the paths and environment stuff set up.

You do not seem to have a shell defined in your script, have a look at other scripts in /etc/init.d for examples of how they are structured.[/QUOTE]

Hi DcStar,

I have had a look and placed a path statement at the top of the script. Is this what you wanted me to try or is there more to it? I have had a look through some of those files and have yet to stumble accross one that defines a shell. I'm sure I'm missing something. Is there a particular file in that dir that you suggest I look at?

Regards,

Paul.

---

### Post by dcstar on 2006-02-01
[QUOTE=matouka]Hi DcStar,

I have had a look and placed a path statement at the top of the script. Is this what you wanted me to try or is there more to it? I have had a look through some of those files and have yet to stumble accross one that defines a shell. I'm sure I'm missing something. Is there a particular file in that dir that you suggest I look at?

Regards,

Paul.[/QUOTE]
Every single file in that directory has something based on the following:
```

**#! /bin/sh**
#
# skeleton	Example initscript
#		This file should be used to construct scripts to be
#		placed in /etc/init.d.
#
# Author:	Miquel van Smoorenburg <miquels@cistron.nl>.
#		Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
#		Please remove the "Author" lines above and replace them
#		with your own name if you copy and modify this script.
#
# Version:	@(#)skeleton  2.85-23  28-Jul-2004  miquels@cistron.nl
#

set -e

**PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin**

```
I suggest you put the first and last lines in your script, and see if it makes any difference.

---

