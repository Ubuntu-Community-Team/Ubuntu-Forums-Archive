---
title: "rsync commands to sync localhost with EC2 instance"
date: 2012-09-05
forum: General Help
---

### Post by dragonfly41 on 2012-09-05
I'm setting up a batch of rsync scripts to sync my localhost /var/www
to the equivalent server in an EC2 instance and I need to understand the finer points of the rsync syntax.

I've first read [COLOR=Navy]man rsync[/COLOR]

As I understand rsync .. this following command copies "/var/www/" (with trailing slash) into destination EC2 (ubuntu) instance

```
rsync -avz /var/www/ -e  "ssh -i ~/.ec2/myprivatekey.pem" ubuntu@ec2-xx-xxx-xxx-xx.eu-west-1.compute.amazonaws.com:/var/www
```

Is it correct to leave off the trailing slash on destination?

as in man rsync ...

rsync -av /src/foo/ /dest/foo      [COLOR=Red]<<< no trailing slash[/COLOR]

What is the rsync command if copying _individual files_ (e.g. test.php) rather than recursively copying directories?

e.g. is this correct?

```
rsync -avz /var/www/test.php -e  "ssh -i ~/.ec2/myprivatekey.pem" ubuntu@ec2-xx-xxx-xxx-xx.eu-west-1.compute.amazonaws.com:/var/www
```
or this correct with a colon separating the host name and file path to test.php

```

rsync -avz /var/www:test.php -e  "ssh -i ~/.ec2/myprivatekey.pem" ubuntu@ec2-xx-xxx-xxx-xx.eu-west-1.compute.amazonaws.com:/var/www
```[COLOR=Navy]
[/COLOR]
Should I be considering use of --include and --exclude args?

---

### Post by Habitual on 2012-09-05
I think the safe bet is to always end with a trailing slash. I could be wrong (I frequently am at this hour).

Other more informed opinions and advice will surely follow. 

Have a Great Day!

---

### Post by LewisTM on 2012-09-05
The trailing slash in the destination can be left out. It is meaningful for the source, it means "Copy the directory contents inside..." (slash) instead of "Copy the directory _and_ it's contents to..." (no slash).

For the single file, your first example is the right one.

Cheers!

---

### Post by dragonfly41 on 2012-09-05
Thanks .. I'll start trying out some rsync commands on EC2 ..

I've read a bit more and there is an argument **[COLOR=Navy]--dry-run [/COLOR]**which allows a simulated run of rsync commands.

and **[COLOR=Navy]--log-file=FILE[/COLOR]** for logging

---

### Post by dragonfly41 on 2012-09-05
I've been testing commands but still hitting some problems

Firstly I can launch a ssh session into my remote EC2 instance and run commands on EC2 server so that part is o.k

but when i try to either send  /var/www
from localhost to EC2
or 
from EC2 to localhost

I'm having a problem

[COLOR=Navy]sudo ssh -i ~/.ec2/mykey.pem  [email]ubuntu@ec2-xx-xxx-xxx-xx.eu-west-1.compute.amazon/myaws.com[/email]:/var/www/   /var/www/[/COLOR]

[COLOR=DarkRed][xx,xxx.xxx.xx is my AWS static IP address][/COLOR]

I get this error in terminal
[COLOR=Navy]
Unexpected remote arg: [email]ubuntu@ec2-xx-xxx-xxx-xx.eu-west-1.compute.amazonaws.com[/email]:/var/www/
rsync error: syntax or usage error (code 1) at main.c(1222) [sender=3.0.7][/COLOR]


In the opposite direction .. /var/www/ in localhost > /var/www/ in EC2 .. I get this error

[COLOR=Navy]ssh: Could not resolve hostname ec2-xx-xxx-xxx-xx.eu-west-1.compute.amazonaws.com:/var/www: Name or service not known[/COLOR]


I can use FileZilla as client to connect to EC2 using the same key and I can see /var/www/ in the EC2 instance and move files by FileZilla.   But I need to get rsync working to and fro.

---

### Post by papibe on 2012-09-05
Hi dragonfly41.

AFAIN, vanilla rsync is not supported by Amazon (I may be mistaken though, could you post a link where says it does?).

There are several rsync-like alternatives that support S3 storage as backend. The ones I've read:  s3fs, s3sync, s3command, s3cp, tarsnap, duplicity, etc.

Sources: [here]("http://superuser.com/questions/288270/can-i-use-rsync-for-backing-up-at-amazon-s3"), [here]("http://blog.eberly.org/2008/10/27/how-i-automated-my-backups-to-amazon-s3-using-rsync/") and [here]("http://serverfault.com/questions/73959/using-rsync-with-amazon-s3").

Regards.

---

### Post by dragonfly41 on 2012-09-05
Papibe

I'm fairly sure that rsync is supported by Amazon .. rsync in FileZilla works .. 

Note I'm using EC2 not S3.

I'm beginning to guess that this problem relates to users/permissions

I've just used ssh to inspect the /vars/ folder in EC2 instance and this is what I see

```
ubuntu@ip-xx-xx-xx-xx:~$ cd /var
ubuntu@ip-xx-xx-xx-xx:/var$ ls -l
total 16
drwxr-xr-x  2 root root  4096 2011-11-18 06:25 backups
drwxr-xr-x 13 root root  4096 2011-11-17 21:08 cache
drwxr-xr-x 45 root root  4096 2011-11-20 06:47 lib
drwxrwsr-x  2 root staff    6 2010-10-07 09:15 local
drwxrwxrwt  3 root root    60 2012-09-05 06:25 lock
drwxr-xr-x 13 root root  4096 2012-09-05 06:25 log
drwxrwsr-x  2 root mail     6 2011-03-19 06:28 mail
drwxr-xr-x  2 root root     6 2011-03-19 06:28 opt
drwxr-xr-x 12 root root   480 2012-09-05 21:33 run
drwxr-xr-x  4 root root    43 2011-03-19 06:30 spool
drwxrwxrwt  2 root root     6 2010-10-07 09:15 tmp
drwxr-xr-x  5 root root    66 2011-11-17 16:11 www
ubuntu@ip-xx-xx-xx-xx:/var$
```Should I change the ownership of /var/www from "root" to "ubuntu"?

[COLOR=DarkRed][p.s.]

Here is just one thread I've read .. as you asked ..

[http://www.freewisdom.org/photos/2008/09/17/backup_with_rsync/](http://www.freewisdom.org/photos/2008/09/17/backup_with_rsync/)


[edit]

Last attempt before signing off tonight was to try changing ownership of /var/www on EC2 to ubuntu / ubuntu

[http://stackoverflow.com/questions/11268486/aws-ec2-ftp-html](http://stackoverflow.com/questions/11268486/aws-ec2-ftp-html)

sudo chown -R ubuntu /var/www

sudo chgrp -R ubuntu /var/www

sudo chmod g+w /var/www


but still getting errors.



[/COLOR]

---

### Post by LewisTM on 2012-09-05
> sudo ssh -i ~/.ec2/mykey.pem [email]ubuntu@ec2-xx-xxx-xxx-xx.eu-west-1.c...azon/myaws.com[/email]:/var/www/ /var/www/
I'm not sure about this command, there must be a typo. [FONT="Courier New"]sudo ssh -i ...[/FONT] is not an rsync command.
Also the address is malformed
[email]ubuntu@ec2-xx-xxx-xxx-xx.eu-west-1.compute.amazon/myaws.com[/email]:/var/www
should be 
[email]ubuntu@ec2-xx-xxx-xxx-xx.eu-west-1.compute.amazonaws.com[/email]:/var/www

---

### Post by dragonfly41 on 2012-09-06
You're quite right .. that last command I posted was screwed up .. incorrect .. I was getting tired at that point.

I've been reading further and found quite a few threads with the error string .. [COLOR=Navy]

[/COLOR]```
Unexpected remote arg:
```this thread refers to nested quotes .. 

[http://www.linuxquestions.org/questions/linux-server-73/rsync-with-irregular-ssh-remote-port-and-non-root-user-934062/](http://www.linuxquestions.org/questions/linux-server-73/rsync-with-irregular-ssh-remote-port-and-non-root-user-934062/)

and gave some suggestions.

Finally I read about[COLOR=Navy] the GUI  **luckybackup**[/COLOR] (in Synaptic Package Manager) and using this GUI I was able to setup backup commands using rsync+ssh session > EC2

[http://luckybackup.sourceforge.net/manual.html](http://luckybackup.sourceforge.net/manual.html)

luckybackup allows dry runs and the compiled rsync+ssh command (from the GUI) can be viewed.

Scheduler allows cron to be used.

Note that luckybackup flags up permissions errors of the key if the key too open and I had to apply **[COLOR=Navy]chmod 600[/COLOR]** to the key.

I also updated rsync to rsync  version 3.0.9 for good measure (ubuntu installs 3.0.7 as default).

---

