---
title: "Accidently removed /var/lib"
date: 2009-09-08
forum: General Help
---

### Post by jav on 2009-09-08
I intended to run 
```
"sudo -r /var/lib/<package>"
```
however, instead I ran
```
"sudo -r /var/lib"
```

The consequence now is that whenever I run e.g.
```
sudo apt-get install <package>
```
I get the output
```
E: Could not open lock file /var/lib/dpkg/lock - open (2 No such file or directory)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

What can I do to fix this (other than deleting everything and reinstalling)?
I'm running Ubuntu Server, Hardy Heron (8.04).

Is it perhaps possible to somehow do an
```
dpkg-reconfigure <some_magic_flag> | <all my packages>
```
or some thing similar?

---

### Post by jav on 2009-09-08
Some updates.

```
$ dpkg --list
dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
```

```
$ sudo dpkg-reconfigure apt-get
dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: apt-get is not installed
```

```
$ sudo dpkg-reconfigure apt
dpkg-query: failed to open package info file `/var/lib/dpkg/status' for reading: No such file or directory
/usr/sbin/dpkg-reconfigure: apt is not installed
```

---

### Post by arrange on 2009-09-08
> **jav said:**
> I intended to run 
```
"sudo -r /var/lib/<package>"
```
however, instead I ran
```
"sudo -r /var/lib"
```
Are you sure? ```
arrange@lean:/var/lib$ sudo -r /var/lib
sudo: illegal option `-r'
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
```

Did you run ```
sudo rm -r /var/lib
```instead? What does ```
ls -l /var/lib
```say? Is there really nothing there?

---

### Post by jav on 2009-09-08
```
ls /var/
```

gives

```
agentx   cache  games  lock  mail  run    tmp
backups  crash  local  log   opt   spool  www
```

The "lib" directory is **gone**.

---

### Post by arrange on 2009-09-08
What's the contents of */var/lib/backups*? You should be able to find *dpkg.status.0* - backup file there. First restore */var/lib/dpkg* - see [this script example]("http://qref.sourceforge.net/Debian/reference/examples/debian-package-database-rebuild") (just for reference!) and then reinstall important/all packages in your system.

Are you able to find your way around in that script?

---

### Post by P4man on 2009-09-08
since /var/lib is gone, /var/lib/backups won't exist either.

I think the OP has a serious problem, Im not sure there is a way to recover from that easily without reinstalling. Perhaps copying /var/lib from a live cd *might* get it working well enough to be able to run aptitude again, but I have no idea  :s

---

### Post by arrange on 2009-09-08
> **P4man said:**
> since /var/lib is gone, /var/lib/backups won't exist either.
Oops, sorry, it's */var/backups/dpkg.status.0*, NOT */var/lib/backups/...*!

I think you should give it a try.

---

### Post by jav on 2009-09-08
I do have some contents in /var/backups/

```
ls /var/backups/ |grep -i dpkg
dpkg.status.0
dpkg.status.1.gz
dpkg.status.2.gz
dpkg.status.3.gz
dpkg.status.4.gz
dpkg.status.5.gz
dpkg.status.6.gz

```

From what I gather from the script linked to above I need to modify that script to use my own dpkg.status.0 rather than it's own rudimentary version.

I'll give it a try.

---

### Post by jav on 2009-09-08
Ok.
It seems as if my first hindrance is that "sudo" is broken.
I can't sudo.

```
$ sudo ls
[sudo] password for jav: 
Aborted
```

---

### Post by wojox on 2009-09-08
I think your looking at a reinstall jav. Hate to say it but there were so pretty important files in there. See what you can back up from home first.

---

### Post by arrange on 2009-09-08
I've just tested it out: I removed my */var/lib* directory and was able to recover. Basically I just created a few stub directories, copied the status file backup, and did a **dselect update**. Then reinstalled a few programmes that had directories in /var/lib. I encountered a few problems, but overall it seems to work.

On the other hand, I was not able to reproduce the sudo problem, but I think they're not connected.

If you're still interested, I can post more details.

But still, backup of your /home and reinstall seems much easier.

---

### Post by marco.org on 2010-09-07
Firstly, you don`t must scare to restart your operating system. I restarted it and it works after restart fine :)
Patient provided me to successfuly repairing my Debian.

```
dpkg --configure -a
``` did not work for me,  unfortunelly.

In default directory /var/backups/ there are some files, which can help you. I copied dpkg.status.0 into /var/lib/dpkg/ with changed name to status.

Directories needed (you must create it using mdkir):
```

mkdir /var/lib/dpkg/alternatives/  /var/lib/dpkg/info/  /var/lib/dpkg/methods/  /var/lib/dpkg/parts/  /var/lib/dpkg/  triggers/  /var/lib/dpkg/updates/  /var/lib/apt/  /var/lib/aptitude  /var/lib/binfmts/  /var/lib/misc/ 
```
and empty files:
```

touch /var/lib/dpkg/available

```
Maybe some other files too, but I made experiments with all changes (I doesn`t want to reinstall my Debian simply like Windows :) ) and I'm remebered it. It is necessary: You must read all output in tty.

After that I permoformed ```
aptitude update && aptitude upgrade
```
There was many warnings from dpkg:

```

dpkg: warning: brak listy plików pakietu "mount", przyj&#281;cie &#380;e pakiet nie ma zainstalowanych plików.
dpkg: warning: brak listy plików pakietu "kadu-common", przyj&#281;cie &#380;e pakiet nie ma zainstalowanych plików.

```

All these warnings was in /var/log/apt/term.log
I wrote simle script warnings.sh (chmod 711 warnings.sh):

```

#!/bin/bash
cd /var/log/apt
cat term.log | grep "warning" > warning.txt
cat warning.txt | awk '{print $7}' | sort | uniq > packets
sed -e 's/\"/ /g' packets > packets.2
sed -e 's/,/ /g' packets.2 > packets.3
echo `cat packets.3` > packets.4

```

after that I had in packets.3 all listed packets one per line and in packets.4 all in one line. It is possible to do it in one command, but I'm don't scare about it...
I performend many times aptitude reinstall `cat packets.3 | grep something` 
(something was instead of e.g. lib (my suggest is to that the first one), xorg, xserver, kde)
When I had failures with any package, I removed it with aptitude remove this_packet :) In all cases failure was due to installed by me other software from compiled source code or other commercial software (not existed in Debiaan repository)

What I can say now.

My Debian works fine. I lost a lot of time, faster is make backup of the most worth files and reinstall it :) but all things, what I done, make my Debian stable again (I'm using Debian 5.0\testing still) :)

PS. 
My friend said, that he would not admit to this mistake: rm -rf /var/lib/* 
I think, that nobody is perfect (but I`m pretty ****ing close).

Please, let me know about issues to [email]marco.org@interia.pl[/email] 

PS2.
Ubuntu is like Debian and this post can help you in repairing your Ubuntu OS.

Best regards,
marco.org

---

