---
title: "Home directory is locked"
date: 2010-01-19
forum: General Help
---

### Post by rpaskudniak on 2010-01-19
Hi again, family.

I recently realized, to my annoyance, that my old UPS no longer does even the task of a surge suppressor!](*,)  The obvious casualty of this discovery seems to have been my home directory.  After running fsck on it (in recovery shell) **_I cannot create a file in my home directory_** or anywhere below it.  This is the case even if I try it as root, so simply setting permissions don't cut it.

I have tried setting permissions using the Ubuntu file browser; I have included screen shots of the dialog box before and after I have tried to set permissions this way.  (I have cut off the titles to avoid revealing my true name, though my login name does show.) The change shown has no effect.  In fact, when I close & reopen the properties window it goes back to the first state.

In the shell, if I try to create a file using [FONT="Courier New"]>>[/FONT], I get this:
```
~$ >>xxx
bash: xxx: Invalid argument
~$ echo $?
1
```
If I try it under ksh, I at least get a more understandable error message:
```
ksh: xxx: cannot create [Invalid argument]
```
The exit code is 1 here also.  This might the catch-all failure code or it might really be ENOPERM.

[SIZE="4"]**HELP!**[/SIZE]  My login is useless in this state! :frown:  Creating another user as a kludge is fraught with side issues and I would never go that path if I were managing Linux in a commercial environment.

So how do I pinpoint the blockage and how to I fix it?

Thanks much!

---

### Post by michy99 on 2010-01-19
Is /home on a separate partition?

---

### Post by rpaskudniak on 2010-01-19
michy99,
Yes, my /home is the mount directory of a large partition.  FWIW, my 3 Ubuntu partitions are:
[FONT="Courier New"]/swap
/ (The root)
/home[/FONT]

My reasons for this odd arrangement are related to the age of my BIOS.

BTW, the two other user home directories have no problem.  Only this one (which was open at the time of the damaging outage) is damaged as described.

---

### Post by rpaskudniak on 2010-01-31
SIGHhh...
OK, it took one more reboot with fsck to remove the problem.  This time, I remembered to run the fsck under the script command.  Some interesting output from the beginning:
> Pass 1: Checking inodes, blocks, and sizes
Inode 745810 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 745812 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

Inode 745814 has EXTENTS_FL flag set on filesystem without extents support.
Clear? yes

BTW, I ran the command: [FONT="Courier New"]fsck -yV /dev/sda4[/FONT]; that's where my /home is mounted.

There were more error messages, of course, but these caught my eye up front because they involve corrupt flags.

I ran this command to locate which files these were:
```
[FONT="Courier New"][SIZE="1"]find / -inum 745810 -o -inum 745812 -o -inum 745814 | xargs ls -ilda[/SIZE][/FONT]
```
in retrospect, I should have specified to start the find in /home but I'll save that hindsight for next time.  Here's the output for /, allowing for the repeated inone numbes in different file systems:
> [FONT="Courier New"]745814 -rw------- 1 informix informix  222 2010-01-30 22:20 /home/informix/.gconf/apps/gnome-screensaver/%gconf.xml
745812 -rw-r--r-- 1 informix informix 7511 2010-01-30 22:20 /home/informix/.xscreensaver
745810 -rw-r--r-- 1 root     root     1844 2009-04-16 23:43 /lib/firmware/2.6.28-11-generic/sb16/ima_adpcm_capture.csp
745812 -rw-r--r-- 1 root     root     1872 2009-04-16 23:43 /lib/firmware/2.6.28-11-generic/sb16/ima_adpcm_playback.csp
745814 -rw-r--r-- 1 root     root     2253 2009-04-16 23:43 /lib/firmware/2.6.28-11-generic/sun/cassini.bin
[/FONT]
Why the informix files were corrupted I can't guess; I was not logged as informix at the time of the crash.

Some lingering problems remain, as discovered in the "find" error output but those loose ends will go into another thread.

For now, _this_ problem is solved. :-\"

---

