---
title: "running script at shutdown"
date: 2010-04-27
forum: General Help
---

### Post by murraypatterson on 2010-04-27
Hi, so I want to run the following script at shutdown:

```

#! /bin/sh

rsync -avz ~/ /mnt/barracuda/backup

```

to backup my files to my second hard drive "barracuda", so I named the above script "backup.sh" and placed it in /etc/init.d and gave it full execute access (as per the other scripts in init.d, such as kerneloops, for example).  Now ls -l backup.sh gives:

```

-rwxr-xr-x 1 root root 48 2010-04-27 01:09 backup.sh

```

then, in /etc/rc0.d, I created the following symlink:

```

ls -s K10backup.sh ../init.d/backup.sh

```

however, when I shutdown the computer, the script does not run.  From all the reading online I cannot see what has gone wrong, but clearly something is . . . any help :confused:

---

### Post by rnerwein on 2010-04-27
hi
think the man pages of: 
man update-rc.d  and
man insserv
will help you

ciao

---

### Post by klemes on 2010-04-27
Correct me if I am wrong but I think in the ln -s command syntax you got things the other way around.
It should be ln -s /etc/init.d/backup.sh /etc/rc0.d/K10backup.sh
By issuing the command you wrote you simply overwrote your bash script file with a symbolic link pointing to a non-existent target.
You can confirm this by typing ls -l /etc/init.d/backup.sh and ls /etc/rc0.d/K10* should output file not found....

---

### Post by murraypatterson on 2010-04-27
> **klemes said:**
> Correct me if I am wrong but I think in the ln -s command syntax you got things the other way around.
It should be ln -s /etc/init.d/backup.sh /etc/rc0.d/K10backup.sh
By issuing the command you wrote you simply overwrote your bash script file with a symbolic link pointing to a non-existent target.
You can confirm this by typing ls -l /etc/init.d/backup.sh and ls /etc/rc0.d/K10* should output file not found....

it seems to have linked properly, i.e., this is what I get:

```

ls -l /etc/rc0.d/K10backup.sh 

lrwxrwxrwx 1 root root 19 2010-04-27 01:25 /etc/rc0.d/K10backup.sh -> ../init.d/backup.sh

```

thanks though

Cheers,
Murray

---

