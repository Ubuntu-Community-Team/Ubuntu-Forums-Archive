---
title: "Cron job file and rkhunter.log"
date: 2012-09-16
forum: General Help
---

### Post by UltimateCat on 2012-09-16
I clicked on my file system and typed in my root password and began to follow the path to my cron jobs file; var/spool/cron/root.
Trying to look at the cron file a window opened in red with:
```
You do not have permissions necessary

```Two very disturbing things happened.  I discovered that I do not have the /root file and I was given a 'Warning'
Why the warning?.....I did sign in as root-

When I ran <#cat /var/log/rkhunter.log> in the terminal the output was:
 " [23:05:50] Warning: Hidden directory found: /etc/.java
 " [23:05:50] Warning: Hidden directory found: /dev/.udev
 " [23:05:50] Warning: Hidden directory found: /dev/.initramfs

" [23:05:50] Possible rootkits: 2
" [23:05:50] Rootkit names    : Xzibit Rootkit, Xzibit Rootkit

Is this serious? 
If so what do I need to do?

---

### Post by UltimateCat on 2012-10-07
I think it is a false-positive but I don't know how to check-
How do I tell since the file says:
You do not have permissions necessary
Also, I have been studying the Shell Scripting Guide because I have never writen a script before.  I'm trying to learn so I can have a script for cron jobs for rkunter and chrootkit.  Here's were I started:
 [http://mywiki.wooledge.org/BashGuide/Parameters](http://mywiki.wooledge.org/BashGuide/Parameters)

Where else could I learn about shell scripting?

---

