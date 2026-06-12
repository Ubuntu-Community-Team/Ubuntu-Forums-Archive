---
title: "I get mail -- but noone else"
date: 2011-10-04
forum: General Help
---

### Post by AlexBooton on 2011-10-04
Hi,

I'm stumped.  I can access the postfix server to read my mail.

BUT I'm the only user that can.

Everyone else get rejected.

Here's the syslog entry for another user:
...dovecot: pop3-login: Disconnected (auth failed, 1 attempts): user=<jmarino>, method=PLAIN, rip=192.168.0.51, lip=192.168.0.189

And here's an entry for me:
...dovecot: pop3-login: Login: user=<ed>, method=PLAIN, rip=192.168.0.51, lip=192.168.0.189

So ONLY I am able to get my mail.  And this is consistent.

The other users and passwords are valid.  I've re-set them just to be sure.

I suspect it's a rights issue but I've checked the rights for all /var/mail files and they're all the same except the owner of the file is the actual owner.

I also checked all the rights for the files in /etc/dovecot.  They all look OK and they all have root/root for the owner and user.

Since I installed the system and did all the editing of the configuration files it's possible, but unlikely, that I'm the owner or group of some key file.  I've looked for that but found nothing suspicious.

Is it possible I may have given myself root access?  I don't see how.  My UID is 1000. Does the fact I'm the first user (per my UID) make a difference?  I would think not.

So I'm stumped.  I don't have a clue as to where to look or what to do next.

Any thoughts will be greatly appreciated.

This is U11.04.  A new/clean install.

Thanks

---

### Post by AlexBooton on 2011-10-05
Hi,

I have a second U11.04 machine for testing.  I tried and it has the same problem!

Only I am able to get mail.  The messages in syslog are the same as posted above.  

I forgot to mention I've enabled plain text login. You can see that in the log snippet.

I just don't understand how this can be.  Two people but only one gets mail.  Why?  How?

Thanks

---

### Post by AlexBooton on 2011-10-06
Anyone.  I'm a bit desperate.  

Any thoughts, stabs in the dark, WAGs, etc. gratefully accepted.

---

