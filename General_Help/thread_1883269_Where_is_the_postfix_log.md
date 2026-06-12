---
title: "Where is the postfix log?"
date: 2011-11-18
forum: General Help
---

### Post by Nailox on 2011-11-18
edit: the problem had nothing to do with postfix. thanks for your replies. mods can close the thread if they need to.

---

### Post by dcstar on 2011-11-19
> **Nailox said:**
> I cant find it in /var/log

any ideas?

mail.info
mail.log

You choose.

---

### Post by Nailox on 2011-11-20
root@xxxx:~# find . / -name mail.log
root@xxxx:~# find . / -name mail.info
find . / -name postfix.log
find . / -name maillog

none of those can find anything?

---

### Post by Nailox on 2011-11-20
output is
```
total 100
drwxr-xr-x  7 root  root   4096 2011-11-14 21:22 .
drwxr-xr-x 14 root  root   4096 2010-05-04 20:15 ..
drwxr-x---  2 root  adm    4096 2011-10-17 14:24 apache2
drwxr-xr-x  2 root  root   4096 2010-05-04 20:11 apt
-rw-r-----  1 root  adm       0 2010-05-04 22:12 boot
-rw-rw-r--  1 root  utmp      0 2010-05-04 18:43 btmp
-rw-r-----  1 root  adm       0 2010-05-04 22:12 dmesg
-rw-r--r--  1 root  root  35083 2011-11-20 14:59 dpkg.log
-rw-r--r--  1 root  root  24048 2011-11-14 21:24 faillog
drwxr-xr-x  2 root  root   4096 2010-05-04 18:47 fsck
-rw-rw-r--  1 root  utmp 292584 2011-11-20 14:32 lastlog
drwxr-s---  2 mysql adm    4096 2010-05-04 20:17 mysql
-rw-r-----  1 mysql adm       0 2010-05-04 20:17 mysql.err
-rw-r-----  1 mysql adm       0 2010-05-04 20:17 mysql.log
drwxr-xr-x  2 root  root   4096 2011-11-14 21:27 proftpd
-rw-rw-r--  1 root  utmp  10368 2011-11-20 14:32 wtmp
```

---

### Post by QLee on 2011-11-20
> **Nailox said:**
> root@xxxx:~# find . / -name mail.log
root@xxxx:~# find . / -name mail.info
find . / -name postfix.log
find . / -name maillog

none of those can find anything?

Yo rastamon,

You probably should lay off the ganja while reading the manual page. Your commands search the current directory and, presumably you are not in var/log.

So Ja say!


Edit: Since you appear to be in the root (user) directory you would want a path statement, maybe something like this:
root@xxxx:~# find /var/log/mail.log
/var/log/mail.log

Or maybe I should take my own advice...

---

### Post by Nailox on 2011-11-20
> **QLee said:**
> Yo rastamon,

You probably should lay off the ganja while reading the manual page. Your commands search the current directory and, presumably you are not in var/log.

So Ja say!


Edit: Since you appear to be in the root (user) directory you would want a path statement, maybe something like this:
root@xxxx:~# find /var/log/mail.log
/var/log/mail.log


Or maybe I should take my own advice...
that what you mean? 
```

root@plecode:~# find . /var/log -name mail.log

```
And btw whats your own advice that you shud take? which one of those lol 
Jah bless!

---

### Post by boast on 2011-11-20
maybe check /etc/syslog.conf where it stores mail logs

---

### Post by Nailox on 2011-11-20
> **boast said:**
> maybe check /etc/syslog.conf where it stores mail logs

theres no syslog.conf in /etc

---

### Post by QLee on 2011-11-21
> **Nailox said:**
> theres no syslog.conf in /etc

Yes, that is the old style method a while back Debian migrated to rsyslog so the config file is rsyslog.conf. You could check there.

Unfortunately I won't be able to help with much postfix troubles if this is a problem with that as I use exim for my MTA.

Nailox, what happens when you enter, locate mail.log, into a terminal?

---

### Post by Nailox on 2011-11-21
> **QLee said:**
> Yes, that is the old style method a while back Debian migrated to rsyslog so the config file is rsyslog.conf. You could check there.

Unfortunately I won't be able to help with much postfix troubles if this is a problem with that as I use exim for my MTA.

Nailox, what happens when you enter, locate mail.log, into a terminal?

erm.. nothing. i installed locate but when i enter "locate mail.log" there is no output. I guess Im not using it properly because I can't find anything with locate.. I read the man pages, I tried some strings but nothing.

in /etc there is rsyslog.d but no rsyslog.conf

I found this in /var/spool/postfix/postfix.conf
```
# Create an additional socket in postfix's chroot in order not to break
# mail logging when rsyslog is restarted.  If the directory is missing,
# rsyslog will silently skip creating the socket.
$AddUnixListenSocket /var/spool/postfix/dev/log

```
I don't quite understand this. There's nothing in /var/spool/postfix/dev/log

---

### Post by QLee on 2011-11-21
[QUOTE=Nailox]erm.. nothing. i installed locate but when i enter "locate mail.log" there is no output. I guess Im not using it properly because I can't find anything with locate.. I read the man pages, I tried some strings but nothing.[/QUOTE]

That makes sense according to what you have found, it appears you don't have those files. They do exist on my system, as empty files, but as I mentioned I use exim as MTA and it has its own log directory.


[QUOTE=Nailox]in /etc there is rsyslog.d but no rsyslog.conf[/QUOTE]

I don't know why that might be, is there anything in your rsyslogd directory? Mine is empty.

I only have an install of 10.04 to check and you're likely using a newer version. Since you have postfix in the subject line, perhaps someone will come along with experience that may be helpful. If no one has after 24 hours or so, bump your thread to attract attention. Good luck.

---

### Post by Nailox on 2011-11-21
> **QLee said:**
> That makes sense according to what you have found, it appears you don't have those files. They do exist on my system, as empty files, but as I mentioned I use exim as MTA and it has its own log directory.




I don't know why that might be, is there anything in your rsyslogd directory? Mine is empty.

I only have an install of 10.04 to check and you're likely using a newer version. Since you have postfix in the subject line, perhaps someone will come along with experience that may be helpful. If no one has after 24 hours or so, bump your thread to attract attention. Good luck.

rsyslog.d only has 1 file - postfix.conf with the following content:
```
# Create an additional socket in postfix's chroot in order not to break
# mail logging when rsyslog is restarted.  If the directory is missing,
# rsyslog will silently skip creating the socket.
$AddUnixListenSocket /var/spool/postfix/dev/log

```










Thanks for the help!
If anyone else can help me  - please reply here.

---

### Post by QLee on 2011-11-21
[QUOTE=Nailox]rsyslog.d only has 1 file - postfix.conf with the following content:
```
# Create an additional socket in postfix's chroot in order not to break
# mail logging when rsyslog is restarted.  If the directory is missing,
# rsyslog will silently skip creating the socket.
$AddUnixListenSocket /var/spool/postfix/dev/log

```[/QUOTE]
If I saw something like that I would look in /var/spool/postfix/dev/log to see if if I could make any sense of it.

You don't mention exactly what problem you are trying to track down but  maybe it is a problem with your postfix configuration, and we are back  to waiting for someone with that experience.

---

### Post by Nailox on 2011-11-21
The problem is the mails arent delivered.Check the 1st post. Strange because it was working a few days ago and then it just stopped and I havent changed anything. There is also the program pflogsum that reads postfix log but i havent installed it b/c i read about some problems with it and I dont want to run into any more trouble. I also found this but it doesnt make much sense to me [http://permalink.gmane.org/gmane.mail.postfix.user/202617](http://permalink.gmane.org/gmane.mail.postfix.user/202617)

---

### Post by boast on 2011-11-21
> **Nailox said:**
> erm.. nothing. i installed locate but when i enter "locate mail.log" there is no output. I guess Im not using it properly because I can't find anything with locate.. I read the man pages, I tried some strings but nothing.


usually have to do "sudo updatedb" first

---

### Post by Nailox on 2011-11-21
> **boast said:**
> usually have to do "sudo updatedb" first

still nothing. I also run apt-get update

---

