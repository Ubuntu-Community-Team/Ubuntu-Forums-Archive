---
title: "Strange crond behaviour and ecryptfs?"
date: 2011-08-03
forum: General Help
---

### Post by chraswiss on 2011-08-03
I am running Natty:
chas@tosh:~$ uname -a
Linux tosh 2.6.35-27-generic #48-Ubuntu SMP Tue Feb 22 20:25:29 UTC 2011 i686 i686 i386 GNU/Linux) 

and am trying to set-up a cron job to run a backup script once per hour.  However the backup script is consistently being run twice each time the cron daemon triggers it for one non-root user 'chas'.  For another non-root user, 'dave' on the same machine the script is run once only (the correct behaviour).

In order to trace the bug I have removed the backup script entirely and instead run an echo once per minute, outputting username and date to a log file for debug purposes.   

chas@tosh:~$ sudo cat /etc/cron.d/crontest 
* * * * *   chas	echo "$(whoami) - $(date)" >> /var/tmp/crontest.log
* * * * *   dave	echo "$(whoami) - $(date)" >> /var/tmp/crontest.log

The only other file at this location is /etc/cron.d/anacron, which remains as it was when first installed.

I have turned off crontabs for all standard users and for root:

chas@tosh:~$ crontab -l
no crontab for chas

dave@tosh:~$ crontab -l
no crontab for dave

chas@tosh:~$ sudo crontab -l
no crontab for root

Here is what I see in the crontest.log:

chas@tosh:~$ cat /var/tmp/crontest.log 
dave - Wed Aug  3 20:31:02 BST 2011
chas - Wed Aug  3 20:31:02 BST 2011
chas - Wed Aug  3 20:31:02 BST 2011
dave - Wed Aug  3 20:32:01 BST 2011
chas - Wed Aug  3 20:32:01 BST 2011
chas - Wed Aug  3 20:32:01 BST 2011
dave - Wed Aug  3 20:33:01 BST 2011
chas - Wed Aug  3 20:33:01 BST 2011
chas - Wed Aug  3 20:33:01 BST 2011

and here's the content of syslog for the same period:

chas@tosh:~$ grep CRON /var/log/syslog
Aug  3 20:31:01 tosh CRON[12259]: (dave) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)
Aug  3 20:31:02 tosh CRON[12262]: Skipping automatic eCryptfs mount
Aug  3 20:31:02 tosh CRON[12263]: (chas) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)
Aug  3 20:31:02 tosh CRON[12267]: (chas) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)
Aug  3 20:32:01 tosh CRON[12292]: (dave) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)
Aug  3 20:32:01 tosh CRON[12294]: Skipping automatic eCryptfs mount
Aug  3 20:32:01 tosh CRON[12296]: (chas) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)
Aug  3 20:32:01 tosh CRON[12300]: (chas) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)
Aug  3 20:33:01 tosh CRON[12325]: (dave) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)
Aug  3 20:33:01 tosh CRON[12327]: Skipping automatic eCryptfs mount
Aug  3 20:33:01 tosh CRON[12329]: (chas) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)
Aug  3 20:33:01 tosh CRON[12333]: (chas) CMD (echo "$(whoami) - $(date)" >> /var/tmp/crontest.log)

So why does crond run chas jobs twice.... and what is that "Skipping automatic eCryptfs mount" entry just before the double trigger?  This might be a red-herring as chas also has a non-auto-mounted Private directory in his home dir ([https://bugs.launchpad.net/ecryptfs/+bug/521222](https://bugs.launchpad.net/ecryptfs/+bug/521222)).

Thanks for reading this far.  All input welcomed.

---

### Post by chraswiss on 2011-08-03
Ok, so I did a bit more research into that strange ecryptfs line and found a verified problem between pam, ecryptfs and cron.

Commenting out the line:

session optional pam_ecryptfs.so unwrap 

in

/etc/pam.d/common-session-noninteractive

fixes the problem but I have slightly different ecryptfs functionalty on my Private folder.

---

