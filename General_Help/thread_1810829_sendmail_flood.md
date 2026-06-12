---
title: "sendmail flood"
date: 2011-07-23
forum: General Help
---

### Post by Grag on 2011-07-23
Hello.
In /var/log/syslog i see that sendmail every 2 minutes sent some messages to user@localhost, www-data@localhost and root.. it's look like:

> Jul 24 02:00:02 localhost sendmail[7836]: p6NM02J9007836: from=root, size=588, class=0, nrcpts=1, msgid=<201107232200.p6NM02J9007836@localhost.localdomain>, relay=root@localhost
Jul 24 02:00:02 localhost sendmail[7840]: p6NM02Am007840: from=www-data, size=1444, class=0, nrcpts=1, msgid=<201107232200.p6NM02Am007840@localhost.localdomain>, relay=www-data@localhost
Jul 24 02:00:02 localhost sm-mta[7837]: p6NM02Ks007837: from=<root@localhost.localdomain>, size=876, class=0, nrcpts=1, msgid=<201107232200.p6NM02J9007836@localhost.localdomain>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Jul 24 02:00:02 localhost sendmail[7836]: p6NM02J9007836: to=root, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30588, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p6NM02Ks007837 Message accepted for delivery)
Jul 24 02:00:02 localhost sm-mta[7843]: p6NM02Bx007843: from=<www-data@localhost.localdomain>, size=1740, class=0, nrcpts=1, msgid=<201107232200.p6NM02Am007840@localhost.localdomain>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Jul 24 02:00:02 localhost sendmail[7840]: p6NM02Am007840: to=www-data, ctladdr=www-data (33/33), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=31444, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p6NM02Bx007843 Message accepted for delivery)
Jul 24 02:00:03 localhost sm-mta[7845]: p6NM02Bx007843: to=<www-data@localhost.localdomain>, ctladdr=<www-data@localhost.localdomain> (33/33), delay=00:00:01, xdelay=00:00:00, mailer=local, pri=31984, dsn=2.0.0, stat=Sent
Jul 24 02:00:03 localhost sm-mta[7844]: p6NM02Ks007837: to=<root@localhost.localdomain>, ctladdr=<root@localhost.localdomain> (0/0), delay=00:00:01, xdelay=00:00:00, mailer=local, pri=31112, dsn=2.0.0, stat=Sent
Jul 24 02:00:08 localhost sendmail[7884]: p6NM08J2007884: from=user, size=2558, class=0, nrcpts=1, msgid=<201107232200.p6NM08J2007884@localhost.localdomain>, relay=user@localhost
Jul 24 02:00:09 localhost sm-mta[7885]: p6NM08Ka007885: from=<user@localhost.localdomain>, size=2846, class=0, nrcpts=1, msgid=<201107232200.p6NM08J2007884@localhost.localdomain>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Jul 24 02:00:09 localhost sendmail[7884]: p6NM08J2007884: to=user, ctladdr=user (1000/1000), delay=00:00:01, xdelay=00:00:01, mailer=relay, pri=32558, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p6NM08Ka007885 Message accepted for delivery)
Jul 24 02:00:09 localhost sm-mta[7886]: p6NM08Ka007885: to=<user@localhost.localdomain>, ctladdr=<user@localhost.localdomain> (1000/1000), delay=00:00:01, xdelay=00:00:00, mailer=local, pri=33082, dsn=2.0.0, stat=Sent

At the same time start Cron jobs... .sh scripts...

How to forbid send any messages to localhost by sendmail?
Help please.
Sorry my english.

---

### Post by Habitual on 2011-07-23
Edit the crontab using 
```
crontab -e
```
and add
```
> /dev/null 2>&1
```

to the end of the cron entry.

For example:
```
*/5 * * * * /usr/bin/php /var/www/cacti2/poller.php > /dev/null 2>&1
```

---

### Post by Grag on 2011-07-23
Thank you)

---

