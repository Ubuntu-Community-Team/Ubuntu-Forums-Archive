---
title: "Dovecot Install"
date: 2010-03-19
forum: General Help
---

### Post by greppinfunk on 2010-03-19
Hi, 

Should have really posted here first, but I seem to have messed up and am now in a bit of depressing blackhole.

I bought "The Official Ubuntu Server Book" and am following the email server tutorial, I installed PostFix fine, and DoveCot, I then googled around and followed a few other tutorials and ended up in a bit of mess.

Mainly I followed this : [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Anyway, SSL didn't work and the whole thing was acting strangely, I decided to start again, so used apt-get remove and apt-get purge to remove the packages.

I managed to reinstall PostFix straight away by using the apt-get -f install arguement, and PostFix is back up and running. However when trying to install DoveCot I get the following output.

**sudo apt-get install dovecot-imapd dovecot-pop3d**

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
dovecot-imapd is already the newest version.
dovecot-pop3d is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up dovecot-common (1:1.0.10-1ubuntu5.2) ...
Not replacing deleted config file /etc/dovecot/dovecot.conf
Not replacing deleted config file /etc/dovecot/dovecot-ldap.conf
Not replacing deleted config file /etc/dovecot/dovecot-sql.conf
chmod: cannot access `/var/run/dovecot': No such file or directory
dpkg: error processing dovecot-common (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of dovecot-imapd:
 dovecot-imapd depends on dovecot-common (= 1:1.0.10-1ubuntu5.2); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-imapd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dovecot-pop3d:
 dovecot-pop3d depends on dovecot-common (= 1:1.0.10-1ubuntu5.2); however:
  Package dovecot-common is not configured yet.
dpkg: error processing dovecot-pop3d (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dovecot-common
 dovecot-imapd
 dovecot-pop3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So now I'm kind of lost, and googling and reading for over 2 hours has given me very little help, there was a few forums with similar errors, but have no solutions.

Thanks in advanced for any help :)

---

### Post by greppinfunk on 2010-03-19
Found a solution myself and as lot's of searching brings up the same issues for lots of people, I'll post the solution.

The problem arises from apt-get not being able to find the conf files (and claiming they have been deleted), so you can't purge or reinstall, it kind of gets stuck. I've going to do some more testing, but I think this is a bug in apt-get itself.

You need to create the dovecot directory

```
sudo mkdir /etc/dovecot
```

Then create the 3 missing conf files

```
sudo touch /etc/dovecot/dovecot.conf
```
```
sudo touch /etc/dovecot/dovecot-ldap.conf
```
```
sudo touch /etc/dovecot/dovecot-sql.conf
```

The content doesn't matter, as we're deleting them anyway.

This finally lets you purge dovecot

```
sudo apt-get purge dovecot-common dovecot-imapd dovecot-pop3d
```

and now you can reinstall fine

```
sudo apt-get install dovecot-imapd dovecot-pop3d
```

phew... :shock: Now how do we mark this solved...

---

