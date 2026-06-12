---
title: "Please help a 20+ yr MS User"
date: 2009-12-23
forum: General Help
---

### Post by ttoilleb on 2009-12-23
As the title says I have been an MS user since the beginning (and RadioShack TRS-80s before that).  Anyway, I have decided to get off the MS (not so) merry-go-round.  

At this time, I am looking for backup solutions.  On MS I used Robocopy to backup my 2 desktops and 1 laptop to USB drives attached to one of the desktops.  With data, music and web sites scattered everywhere, Robocopy worked very well.  Over the decades I have become quite comfortable with a non-compressed, NON-Sync'ed backup strategy.  That is, if the file has been updated since the last update (8 hr cycle), copy it.  Same if the file does not exist at the backup location.  If I delete a file, it stays on the backup.  No need for versioning either.

I could not find anything that would do that for me (rsync, SBackup, etc) so I developed the followinng script (I know, it is crude but I haven't taught myself shell scripting yet).  And this is where the request for help comes.  The following script will not run all the commands.  It will stop at different points each time I run it.  IE: As if an exit is done  no echo.  I do run it as sudo to get all files.  This script runs on my laptop (9.04) over an 802.11b link.   Each command has been run and works individually, however, it is a pain to comment/uncomment and run multiple times whenever I want to do a backup.

More information directory /_happy is on what I am using as a "file server" - Ubuntu 9.04.  sub-directory /shr-lvbkp is actually a pair of USB drives I LV'ed.

So, what obvious error am I missing?


```

#!/bin/sh -e
#
#    Remember - must run as root
# switches used
#    u (update) - copy only when source is newer than dest
#    v (verbose) - explain what is being done
#    r (recursive) - this directory and all sub-directories
#    f (force) - if dest cannot be opened, remove it and try again
#    P (no-dereference) - never follow symbolic links

echo Begin Backup of etc
cp -ruP /etc /_happy/shr-lvbkp/sleepy

echo Begin Backup of opt
cp -ruP /opt /_happy/shr-lvbkp/sleepy

echo Begin Backup of var
cp -ruP /var/log /_happy/shr-lvbkp/sleepy/var/log

echo Begin Backup of usr
cp -ruP /usr/local /_happy/shr-lvbkp/sleepy/usr/local

echo Begin Backup of home-brage
cp -ruP /home/brage /_happy/shr-lvbkp/sleepy/home

echo Begin Backup of home-common
cp -ruP /home/common /_happy/shr-lvbkp/sleepy/home

echo Begin Backup of home-lampp
cp -ruP /home/lampp /_happy/shr-lvbkp/sleepy/home


exit 0

```Sorry for the runon, but I wanted to give as much info as possible.

---

### Post by oakgrove on 2009-12-23
> This script runs on my laptop (9.04) over an 802.11b link.

Is it possible that the link is dropping from time to time just long enough for the cp to lose its connection and give up but not long enough for you to notice?  Maybe try not doing it wirelessly a few times and using an ethernet cable or something and see if the problem persists.

---

### Post by ttoilleb on 2009-12-23
My kneejerk is that the link is not dropping.  I also ssh into the other pc to check email, status of my boinc queues, etc and have not noticed it dropping.  But, even if it drops the link and terminates the command, would not the ECHO for the next command show?  For example, if the cp for /var is the last one that processes, none of the following echos show in the terminal window.  It just goes to the prompt.

---

### Post by spiderbatdad on 2009-12-23
certainly no bash expert here but i was  thinking:
```
echo Begin Backup of etc
cp -ruP /etc /_happy/shr-lvbkp/sleepy** &&**

echo Begin Backup of opt
cp -ruP /opt /_happy/shr-lvbkp/sleepy** &&**


``` and so on.

---

### Post by oakgrove on 2009-12-23
> But, even if it drops the link and terminates the command, would not the ECHO for the next command show?

Not necessarily.

```

$ sudo strace -o file.txt ./script_to_copy_files.sh

```

When your script craps out, check the last line or two in file.txt for whatever system call it gets hung on.

---

### Post by falconindy on 2009-12-23
Use rsync. Really. It'll do precisely what you want it to do, and it's way better at handling copy operations to a remote computer. It's a little much to comprehend at first, but you'll find that it behaves an awful lot like cp and mv as far as flags and arguments.

Also, programatically, your script is lacking (understandably, so). You can specify multiple sources going to a single destination (for mv, cp, and rsync). For example, I have an rsync backup script that, based on a configuration file, results in the following command:
```
rsync -Rua --delete --stats --exclude-from=/tmp/exclude.conf /etc /home /root /usr/share /var/lib /mnt/Gluttony/backup/quake/
```
All the directories listed (aside from the last one) end up in the final listed directory. The exclude file is also dynamically generated from my config and ignores things such as caches and .git metadata directories. You could just as easily specify multiple --exclude=/path/to flags instead.

I end up with a neat little 'bucket' on my backup drive with the directory structure still in tact (this is helpful so you don't need to think about where to restore a file to -- both from a manual and a scripting perspective.

It hasn't failed me once in the 3 months that I've been using it. Looking back, its ugly (bad) code, but it clearly works.

---

### Post by ttoilleb on 2009-12-26
Ok, I tried the strace.  This is the output

First - terminal messages

```

brage@sleepy:~$ sudo strace -o mybackups.log ./mybackups.sh
[sudo] password for brage: 
Begin Backup of etc
Begin Backup of opt
Begin Backup of var
Begin Backup of usr
Begin Backup of home-brage
cp: cannot create regular file `/_happy/shr-lvbkp/sleepy/home/brage/.mozilla/firefox/ikzy34xr.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/content/xmlhttprequester.js': Permission denied
cp: cannot create regular file `/_happy/shr-lvbkp/sleepy/home/brage/.mozilla/firefox/ikzy34xr.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/content/script-compiler-overlay.xul': Permission denied
cp: cannot create regular file `/_happy/shr-lvbkp/sleepy/home/brage/.mozilla/firefox/ikzy34xr.default/extensions/{c0c9a2c7-2e5c-4447-bc53-97718bc91e1b}/content/prefman.js': Permission denied
cp: cannot stat `/home/brage/.gvfs': Permission denied
brage@sleepy:~$ 

```


Now the strace

```

clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f30f88d3780) = 6841
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6841
--- SIGCHLD (Child exited) @ 0 (0) ---
write(1, "Begin Backup of opt\n"..., 20) = 20
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f30f88d3780) = 6847
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 6847
--- SIGCHLD (Child exited) @ 0 (0) ---
write(1, "Begin Backup of var\n"..., 20) = 20
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f30f88d3780) = 7075
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 7075
--- SIGCHLD (Child exited) @ 0 (0) ---
write(1, "Begin Backup of usr\n"..., 20) = 20
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f30f88d3780) = 7077
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 7077
--- SIGCHLD (Child exited) @ 0 (0) ---
write(1, "Begin Backup of home-brage\n"..., 27) = 27
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f30f88d3780) = 7078
wait4(4294967295, 0x7fffd6f8434c, 0, NULL) = ? ERESTARTSYS (To be restarted)
--- SIGWINCH (Window changed) @ 0 (0) ---
wait4(4294967295, 0x7fffd6f8434c, 0, NULL) = ? ERESTARTSYS (To be restarted)
--- SIGWINCH (Window changed) @ 0 (0) ---
wait4(4294967295, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], 0, NULL) = 7078
--- SIGCHLD (Child exited) @ 0 (0) ---
exit_group(1)                           = ?

```


I didn't post the strace startup messages.  I am gathering that the exit_group(1) is what is killing the script.

---

### Post by switch10 on 2009-12-26
there is a great GUI program that I think you will find really easy.  its called back in time [http://appnr.com/package/backintime-gnome](http://appnr.com/package/backintime-gnome)

---

### Post by ttoilleb on 2009-12-27
Thanks all for your help.  I went with the rsync suggestion.  However, there is still one issue.  The process copied 85,182 of 91,636 files.  Most of the missing files appear to be hidden (.xxxx file names) for system/config.  I am not that concerned about those (it appears they had the rsync chown permission denied (13) error).

However, when looking at the directory, either via ls or nautilus, only the hilevel directories show, no files or sub-directories.  I must go thru sudo to see anything.  all have user=nobody and group=nogroup

command used to copy
```
sudo ./mybackups.sh
```

mybackup.sh contains
```
rsync -Rua --delete --stats --verbose /etc /opt /var /usr/local /home/brage /home/common /home/lampp /_happy/shr-lvbkp/sleepy

```

Before running the process I deleted all files and directories under the sleepy directory.

I guess I am confused why rsync is not copying user/group for the files/directories and why I can see the 1st level sub-directories under sleepy but nothing else as my user.

---

### Post by lykwydchykyn on 2009-12-27
> **ttoilleb said:**
> 
command used to copy
```
sudo ./mybackups.sh
```

mybackup.sh contains
```
rsync -Rua --delete --stats --verbose /etc /opt /var /usr/local /home/brage /home/common /home/lampp /_happy/shr-lvbkp/sleepy

```

Before running the process I deleted all files and directories under the sleepy directory.

I guess I am confused why rsync is not copying user/group for the files/directories and why I can see the 1st level sub-directories under sleepy but nothing else as my user.

First, you want lower-case r, not upper.  Lower-case mean "recursive" which will copy subdirectories.  Upper case means "use relative path names".

Second, do you want to use the "--delete" switch?  In your original description, you said you didn't want to delete files that no longer exist in the source; --delete will cause those files to be deleted.

Third, what file system is on the destination drive?

---

### Post by ttoilleb on 2009-12-27
Ok, first, per the manpage -a, --archive, This is equivalent to -rlptgoD and that covers the recursion, plus copy owner/group parameters

I kept the --delete because it was in the original suggestion for rsync.  I did test the effect of --delete by deleting a file from a source directory.  After the copy it was still in the destination.

As for file system, the following is the entry from fstab
```
# --------------------------------------------------------------------
#  samba shares on happy (shuttle-01)
//192.168.1.94/shr-lvbkp  /_happy/shr-lvbkp  cifs

```

and the fstab for the lv on pc=happy
(actually, the host pc is still named shuttle-01) but when I rebuild it I will change it's name - going for the 7 drawfs)
```
========================================================================================================
# /dev/vgbkp/lvbkp is the lvm dasd for all pcs backups
#
/dev/vgbkp/lvbkp    /_dasd/pc-shuttle-01/lvbkp    ext2    rw,noatime,auto    0    0

```

---

### Post by lykwydchykyn on 2009-12-28
> **ttoilleb said:**
> Ok, first, per the manpage -a, --archive, This is equivalent to -rlptgoD and that covers the recursion, plus copy owner/group parameters

I kept the --delete because it was in the original suggestion for rsync.  I did test the effect of --delete by deleting a file from a source directory.  After the copy it was still in the destination.

Well, that shouldn't be the case, unless you just don't have delete permissions on those files or something else.  If you don't want those files deleted, don't use the --delete flag.

> 
As for file system, the following is the entry from fstab
```
# --------------------------------------------------------------------
#  samba shares on happy (shuttle-01)
//192.168.1.94/shr-lvbkp  /_happy/shr-lvbkp  cifs

```

and the fstab for the lv on pc=happy
(actually, the host pc is still named shuttle-01) but when I rebuild it I will change it's name - going for the 7 drawfs)
```
========================================================================================================
# /dev/vgbkp/lvbkp is the lvm dasd for all pcs backups
#
/dev/vgbkp/lvbkp    /_dasd/pc-shuttle-01/lvbkp    ext2    rw,noatime,auto    0    0

```

Ok, somehow I missed that this was going over a samba connection.  That explains why the user and group are "nobody" and "nogroup".  Your samba must be configured for anonymous access, and consequently you write files to the share as the anonymous user "nobody".

One option to fix this is to mount the samba share using "user" security.  The other, easier option is to have ssh running on the backup machine (I'm guessing it already is) and have rsync directly dump the files over ssh (it can do this without mounting any shares or anything).

The syntax would be:
```

rsync -a sourcefiles 192.168.1.94:/_dasq/pc-shuttle-01/lvbkp/

```

To get that to work without any user interaction, you'd have to set up passwordless/passphraseless ssh key authentication.  If you want to go that route, I'll dig up a tutorial.

---

### Post by ttoilleb on 2009-12-28
I was begining to think that might be the problem.  I had wanted to stay away from the ssh option being unsure about the security since that would expose ssh to the web,  Currently I have ssh requesting a password before the connection is accepted.  But, if I must go the ssh route....  I had already read about the passwordless method and will go back to my notes on that.

lykwydchykyn - Thanks for your help.

---

