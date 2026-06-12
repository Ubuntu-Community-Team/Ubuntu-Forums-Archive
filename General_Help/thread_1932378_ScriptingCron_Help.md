---
title: "Scripting/Cron Help"
date: 2012-02-27
forum: General Help
---

### Post by Warthaug on 2012-02-27
I am faced with an somewhat unusual issue that despite a lot of reading the man files, I cannot figure out how to fix.  Thanx to a recent change in OS/X server, it appears that [it is no longer possible to mount an OS/X share via fstab]("http://askubuntu.com/questions/63046/how-to-mount-mac-osx-lion-file-share").  If that were not enough of a PITA, the OS/X server I am connecting to (for the purpose of nightly backups) goes down on occasion, leading to a loss of connections made via the command line using mount.cifs.  The OS/X computer is not mine, so I have no control over it.

To get around this I was hoping that I could write a script, to be executed by cron, to get around these problems.  What I would like to do is:

1) Check to see if the connection is OK, and if not, reconnect using mount.cifs
2) Run rsync
3) Unmount

My problems are two-fold:
1) I'm not sure how to determine if the connection is up - I was thinking of placing a file in the share and using an if command (if [ -e /osx/test.txt ] to test for its presence, and if missing, run the mount.cifs command.  Is that the best way, or is there a better way to do it?

2) In the event I need to run the mount.cifs command, I need it to be run as root (keep in mind, this is running in cron, so no one is sitting at the keyboard to enter a password).  I cannot figure out how to do this within the script itself, and my one attempt at running a bash script in cron, using 'root' as the user, did not work.  The [ubuntu help file]("https://help.ubuntu.com/community/CronHowto") on chron says to see the man command for more information, but the details in the man crontab has fewer details than the webpage (and not the details I require).

Thank you for any help

Bryan

---

### Post by Warthaug on 2012-02-27
So I have a script that works (using my idea of looking for a file to confirm the connection).  If I run the script using sudo it works perfectly, every time.  However, cron is still giving me headaches.

I've set the script to be owned by root, and tried a few methods to get cron to run it.  I've tried editing the "root" crontab:
```
sudo crontab -e -u root
```
To which I added:
0 12 * * * bash /home/server/configBackup.sh

I also tried adding the above line to the current users cron, as well as adding the above line to the current users cron with a command to run as root:
0 12 * * * root bash /home/server/configBackup.sh

None of these worked.

Any help is appreciated

Bryan

---

### Post by sudodus on 2012-02-27
Try this method which should give response via the loudspeakers

```
sudo crontab -e
``` and enter this text into the editor (cut and paste)
```

# min hour  dom mon dow     command
   *    *    *   *   *      /usr/bin/espeak 'hello world'

```
save and exit the editor. Do the speakers say 'hello world' once every minute? It works for me. If you have no speakers, maybe you can write a file to root's home folder
```
   *    *    *   *   *      /bin/echo 'hello world' > /root/hello.txt
``` and check if it is created every minute.

I think you need the full path to all commands for cron to find them
```
/bin/bash
```

---

### Post by Lars Noodén on 2012-02-27
Rather than cron, maybe [incron](http://inotify.aiken.cz/?section=inotify&page=about&lang=en) could be used to track whether the directory is still mounted or not.

---

### Post by sudodus on 2012-02-27
> **Lars Noodén said:**
> Rather than cron, maybe [incron](http://inotify.aiken.cz/?section=inotify&page=about&lang=en) could be used to track whether the directory is still mounted or not.
I'm reading and learning :-)

---

### Post by Lars Noodén on 2012-02-27
incron is fairly new but it is in the repository.  When I last checked it could not do recursive directories, so you just have to pick a target.  It watches a file or directory until something changes and then does a pre-specified action like cron does for a specific time.

---

### Post by Warthaug on 2012-02-27
Cron is working fine; the script I am using logs its actions into a file, and this logging is occurring at the times specified in cron.  What is not working is running the script as root.

If I enter this into the cron for the current user (i.e. crontab -e):
0 12 * * * root bash /home/server/configBackup.sh

I get the following error (in var/log/syslog), which according to google means the "root" portion of the command is not being found
```
Feb 27 13:43:01 lab-server CRON[2234]: (serverUID) CMD (root bash /home/lab-server/backupShares.sh)
Feb 27 13:43:01 lab-server CRON[2233]: (CRON) error (grandchild #2234 failed with exit status 127)
Feb 27 13:43:01 lab-server CRON[2233]: (CRON) info (No MTA installed, discarding output)
```

If I enter this into the roots cron (sudo crontab -e -u root)
0 12 * * * bash /home/server/configBackup.sh

The script runs, but is not being run as admin, and therefore the script simply detects that it cannot mount the server and exits.  The following error is loged in /var/log/syslog:
```

Feb 27 13:43:01 lab-server CRON[2540]: (root) CMD (bash /home/lab-server/backupShares.sh)
Feb 27 14:10:01 lab-server CRON[2539]: (CRON) info (No MTA installed, discarding output)
```

thanx

Bryan

---

### Post by Lars Noodén on 2012-02-27
One of the easier ways to run the script as root would be to set the cron job as root:

```

sudo crontab -e

```

---

### Post by Warthaug on 2012-02-27
> **Lars Noodén said:**
> One of the easier ways to run the script as root would be to set the cron job as root:

```

sudo crontab -e

```

That has the same effect as sudo crontab -e -u root.  Less typing though.  This is really frustrating, as I've tried entering other commands into the roots cron that require root access to work, and they are working.  This seems to be a specific error due to running a script, rather than running a binary.

Bryan

---

### Post by Warthaug on 2012-02-27
Mystery solved - turns out that cron requires any command that would be run by root to be sudo'd - even if the script is set to run in the root's cron "account".

Many thanx to all who helped

Bryan

---

