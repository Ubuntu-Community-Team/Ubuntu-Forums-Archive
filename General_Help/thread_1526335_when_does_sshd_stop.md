---
title: "when does sshd stop?"
date: 2010-07-07
forum: General Help
---

### Post by RobDonovan on 2010-07-07
I see in /etc/init/ssh.conf that sshd is designed to 

start on filesystem
stop on runlevel S

I understand that runlevel S is single user.
Which says to me that sshd is not stopped on shutdown (runlevel 0).

Also, sshd is in /usr/sbin/sshd and furthermore

sudo lsof -p <sshd_pid>

shows that it uses lib files in /usr/lib.


So, my question is, if sshd is not stopped on shutdown YET sshd uses files in /usr, then how can

/etc/rc0.d/S40umountfs

ever successfully umount /usr during shutdown when /usr is on its own partition? sshd should still be using the files, meaning the file system is busy.  right?

Yet, I'm pretty sure that my shutdowns used to complete successfully.  (Edit : I guess they didn't - see next post)

I'm stumped.  Any suggestions most welcome.

thanks

---

### Post by RobDonovan on 2010-07-08
My conclusion was that sshd never does stop, and never has under Lucid.

This prevents umount from being able to umount /usr if it is on a separate partition and leads to errors like 

umount2: Device or resource busy
umount: /dev/sda7 busy - remounted read-only

in the shutdown console messages.  

I think this is a bug and have filed bug report number 603363.

[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/603363](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/603363)

As I said there, I admit I am by no means an expert on upstart or sshd, but the fix appears to me to be to modify /etc/init/ssh.conf to read 

stop on runlevel [!2345]

Use this fix at your own risk.  I suggest waiting a while and then checking the bug report to see if anyone has said this would be a bad idea.

---

### Post by RobDonovan on 2010-07-17
Since it may be useful to others pursuing umount problems, I'll say how I found out that sshd was still running:

I used the command fuser and later lsof, and also examined /proc/<pid>/maps and /proc/<pid>/cwd.

Since this had to be detected at shutdown, I edited files in /etc/rc0.d/

WARNING : the following edits are dangerous insomuch as if you mess up at all the script will fail when you shutdown your system which may then shutdown with your disks still mounted.  This could result in data loss or disk corruption and make your system unusable, or maybe worse.  Personally I made a copy in my home directory in which I prefixed every potentially destructive command by an echo, tested that as myself to ensure there were no errors, and then made these edits to that file.  I tested that as root.  Only when I was confident did I make the changes to the one that would be used on shutdown.  Proceed at your own risk and be very careful.  

I removed the symbolic link in /etc/rc0.d/S40umountfs and copied the symlink target into it's place, renaming it S40umountfs.   Editing a copy meant I always had the original, and could still reboot my system using the original script (reboot uses the symlink in /etc/rc6.d/) if I wanted to.

I added the following script to the "$VERBOSE = no" section of the "$REG_MTPTS" section of the file, after the 'echo "Unmounting local filesystems"' line but before the umount line, obviously:

```


rm -f /fuser_log
for name in $REG_MTPTS; do
  echo fuser -vm $name >> /fuser_log 2>&1
  fuser -vm $name >> /fuser_log 2>&1
done

rm -f /lsof_log
for name in $REG_MTPTS; do
  echo lsof -U $name >> /lsof_log 2>&1
  lsof -U $name >> /lsof_log 2>&1
done

/ps_script


```and put the following into /ps_script

```


#!/bin/bash

ps -ef > /ps_log 2>&1

rm -f /proc_log
while read line; do
  pid=`echo $line | awk '{print $2}'`
  cmd=`echo $line | awk '{print $8}'`
  if [ "$pid" == "PID" ]; then continue; fi
  echo process $pid $cmd >> /proc_log 2>&1
  ls -l /proc/$pid/cwd >> /proc_log 2>&1
  cat /proc/$pid/maps >> /proc_log 2>&1
done < /ps_log


```then did chmod u+x on /ps_script to make it executable of course.


Now on shutdown details of processes accessing or files open on $REG_MTPTS  partitions (typically those on local disks except /) are written to 

/fuser_log
/lsof_log

details of every process running to 

/ps_log

and details of these processes' /proc/<pid>/cwd and /proc/<pid>/maps files to 

/proc_log


The way this is written, Unix Domain Sockets (including abstract UDSs not tied to any filesystem (but they still have a node number, huh?)) will show up in every lsof_log partition.   Also, fuser_log will always show "mount" in every partition.

sshd showed up in fuser_log under the /usr partition.  I don't think I'd written all the scripts when I did shhd; I suspect it would have showed up in the other logs if I had.

BTW, there are cases where nothing will show up in logs generated using fuser and lsof but still a partition can't be umounted:

I have read that one such case is if NFS has accessed a partition but is not accessing it now, the solution being to restart NFS.

Another, which I discovered myself, is if there is another partition mounted inside the partition you are trying to umount.  This is why /var will not umount during shutdown : because /var/run and /var/lock are still mounted inside it.  I expect to file a bug report on this shortly.

---

