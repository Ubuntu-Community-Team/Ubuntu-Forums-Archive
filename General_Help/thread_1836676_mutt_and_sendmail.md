---
title: "mutt and sendmail"
date: 2011-08-31
forum: General Help
---

### Post by LuniTux on 2011-08-31
Hello,

I have a server that is setup to send email notifications to me when specific events happen. This was working fine until a few days ago. Now for some reason, the emails do not send anymore. I have looked at the log file but can not seem to find a solution.

OS: Ubuntu server 9.10

/var/log/mail.log
```

Aug 31 10:43:31 computername sendmail[541]: p7VEhVGY000541: from=username, size=302, class=0, nrcpts=1, msgid=<20110831144331.GA531@computername>, relay=username@localhost
Aug 31 10:43:32 computername sm-mta[542]: p7VEhWPO000542: SYSERR(root): collect: Cannot write ./dfp7VEhWPO000542 (bfcommit, uid=0, gid=123): No such file or directory
Aug 31 10:43:32 computername sm-mta[542]: p7VEhWPO000542: from=<username@localhost.localdomain>, size=458, class=0, nrcpts=1, proto=ESMTP, daemon=MTA-v4, relay=computername [127.0.0.1]
Aug 31 10:43:32 computername sendmail[541]: p7VEhVGY000541: to=me@myemail.com, ctladdr=username (1000/1000), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=30302, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: 421 4.3.0 collect: Cannot write ./dfp7VEhWPO000542 (bfcommit, uid=0, gid=123): No such file or directory

```

when I try using mutt, it says that the email was sent but I never receive the email.

```
echo "test" | mutt me@myemail.com -s "test"
```

and my /etc/hosts file:

```
127.0.0.1	computername localhost.localdomain localhost
```

---

### Post by LuniTux on 2011-09-02
Hello me,

I have found a solution... sort of.

Remove **sendmail** and install **ssmtp**!

```
sudo apt-get install ssmtp #will automatically remove sendmail
sudo apt-get autoremove #removes sendmail "leftovers"
```

After that

```
sudo nano /etc/ssmtp/ssmtp.conf
```

find these lines and change them.

```
mailhub=<your.host.com>
hostname=<computer name>
```

and, if you are changing the "From Line" uncomment

```
FromLineOverride=YES
```

save & exit

try a test email:

```
echo "Test Body Message" | mutt me@myemail.com -s "Test Subject"
```

---

### Post by LuniTux on 2011-09-02
Thank you, me...

I hope this can help someone else!!!

---

