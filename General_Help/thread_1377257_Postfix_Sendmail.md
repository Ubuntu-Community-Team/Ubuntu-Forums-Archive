---
title: "Postfix Sendmail"
date: 2010-01-10
forum: General Help
---

### Post by Initsil on 2010-01-10
Hey everyone,

I'm simply just having trouble sending mail with postfix.

I have all my hostnames, rdns setup properly.
I also have iptables open on port 25.

Any ideas on how to fix this ASAP is greatly appreciated.

---

### Post by HermanAB on 2010-01-10
Do you have a server account with your ISP? If not, then you need to relay outgoing email through their mail server (google for 'smart host').

---

### Post by Initsil on 2010-01-10
This isn't at my home, this is my web host.

---

### Post by blueridgedog on 2010-01-10
One debugging step is to try and telnet to port 25 of your mail host and verify that you get the mail prompt.

---

### Post by Initsil on 2010-01-10
I think this might be one of the problems.

Postfix doesn't stay running...

```
root@mail:~# /etc/init.d/postfix start
 * Starting Postfix Mail Transport Agent postfix
   ...done.
root@mail:~# /etc/init.d/postfix reload
 * Reloading Postfix configuration...
postfix/postfix-script: fatal: the Postfix mail system is not running
   ...fail!
```

---

### Post by blueridgedog on 2010-01-10
Traditional troubleshooting at this point would be to start the server process, then 

```
tail /var/log/messages
```

and tail the specific postfix log/error file (I don't run it, so I can't point you to it).  Generally when things choke, they tell you why in the log file.

---

### Post by Initsil on 2010-01-10
```
root@mail:/home/plirc/inspircd# /etc/init.d/postfix start
 * Starting Postfix Mail Transport Agent postfix
   ...done.
root@mail:/home/plirc/inspircd# tail /var/log/messages
tail: cannot open `/var/log/messages' for reading: No such file or directory

```

---

### Post by blueridgedog on 2010-01-10
You will need to find out where the log files are on the server you have.  Is there anything in /var/log?

---

### Post by Initsil on 2010-01-10
It doesn't look as if there is anything related to mail in my /var/log. I haven't changed any log directories for postfix.

Here's my ls output of /var/log

```
apache2   btmp        dmesg.0     fsck      mysql      pure-ftpd      user.log
apt       daemon.log  dmesg.1.gz  kern.log  mysql.err  pycentral.log  wtmp
auth.log  debug       dpkg.log    lastlog   mysql.log  syslog
boot      dmesg       faillog     lpr.log   news       udev
```

---

### Post by dcstar on 2010-01-11
```
dpkg-reconfigure postfix
```

---

### Post by Initsil on 2010-01-11
I ran dpkg-reconfigure postfix and I re-ran the install. Postfix does not stay running, and the same as before no logs are found in /var/log.

---

### Post by Initsil on 2010-01-11
Bump

---

### Post by dcstar on 2010-01-12
> **Initsil said:**
> I ran dpkg-reconfigure postfix and I re-ran the install. Postfix does not stay running, and the same as before no logs are found in /var/log.

I forgot to specify that the command should have been run with **sudo**, but what messages were there, what setup selections did you make?

---

### Post by Initsil on 2010-01-12
I was able to get the logs once the mail is sending.

Here is what I got from the output of me trying to send mail to myself.

```
Jan 13 04:17:14 Meshki postfix/qmgr[6825]: A6D7B174131: from=<webmaster@mydomain.info>, size=382, nrcpt=1 (queue active)
```

---

### Post by Initsil on 2010-01-13
Bump.

---

