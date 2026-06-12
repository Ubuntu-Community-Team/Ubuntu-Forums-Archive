---
title: "The joys of crontab"
date: 2011-09-17
forum: General Help
---

### Post by Trunkles on 2011-09-17
Hallo folks.

Server running Natty.

I'm having a little pain with cron. Here's the crontab

```
root@laphroaig:~# crontab -l
# /etc/crontab: system-wide crontab
# Unlike any other crontab you don't have to run the `crontab'
# command to install the new version when you edit this file
# and files in /etc/cron.d. These files also have username fields,
# that none of the other crontabs do.

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# m h dom mon dow user  command
#17 * * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.hourly )
25 6 * * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6 * * 7 root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6 1 * * root test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
05 3 * * * root /etc/init.d/postfix reload
05 10,14,18,22 * * * root dailysync
#0,10,20,30,40,50 * * * * root /usr/bin/woottime >> /home/simon/wootlog
#
```Every time the postifx reload or dailysync jobs try to fire I get an email with 
```
/bin/sh: root: command not found
```in it.
Log in as root and try running either job from the command line and they'll work every time. Just not *** a cron job. ARGH!

---

### Post by Lars Noodén on 2011-09-17
You might try making a script instead and then calling the script from cron.  It seems stupid, but for some reason it is sometimes needed.

Also, be sure there is an extra blank line at the end of the crontab

---

### Post by SeijiSensei on 2011-09-17
Running "crontab -l" as root will return the contents of *root's* crontab, the one stored in /var/spool/cron/root.  For /etc/crontab, you just edit the file directly with an editor.

Notice that user crontabs don't have a username field like /etc/crontab does.  So if the file you list is stored in /var/spool/cron/root, then the cron daemon will consider the sixth field the command to be run, not the name of the user running that command.

That's why you get the "root: command not found" error.

---

### Post by Trunkles on 2011-09-17
...And that makes total sense. A minor edit later and all works perfectly.

Thank you! \\:D/

---

