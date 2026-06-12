---
title: "Sendmail doesn't work either standalone or through fcron"
date: 2011-03-21
forum: General Help
---

### Post by Ralph L on 2011-03-21
I am using fcron on my personal computer running Ubuntu Lucid Lynx to schedule and execute my backups.  Fcron initiates the backup fine.  However, I would also like it to send me an email with the status of the job, when it completes--whether it ran ok or not.  I am unable to make this feature of fcron work.  I am trying to send email on job completion to my normal email account--i.e. the same email account that friends use to send me email.  fcron uses sendmail to send its email.  I also attemped to use sendmail directly, but that didn't work either.   Note:  Because I didn't want to broadcast my email address, I replaced my name in the email with "myemail" in the commands and logs below.

My fcrontab listing (obtain with "fcrontab -l" is:
!mail(true)
!bootrun(true)
!mailto(myemail@mchsi.com),forcemail,mail
& 53 21 * * * export DISPLAY=:0.0&&/home/ralph/lbtest

The log file (syslog) listing from fcron executing using the above setup is
listed below.  Also, I included a log file from executing under Terminal "sendmail [email]myemail@mchsi.com[/email]".  sendmail did not work that way either.  Obviously I don't know how to set up sendmail.  Any help would be appreciated.

Ralph

NOTE:  For anybody reading this to find out how to get fcron to work, please note the command line "export DISPLAY=:0.0" above.  For a long time I could not get my fcron script to show up on the console.  Adding the "export" command fixed that.

NOTE 2:  In order to get sendmail to work without getting a message about my computer name (ralph-laptop) being "not fully qualified" I edited the second line of /etc/hosts to be "127.0.1.1    ralph-laptop ralph-laptop.local" (no quotes).  This added the alias "ralph-laptop.local.  I guess this "qualified" the name ralph-laptop.  Anyway I no longer get the error message and sendmail sends the message immediately rather than waiting a minute and doing a retry.  Hope this information is useful to somebody.

LOG MESSAGES FROM RUNNING fcron.  NOTE THAT sendmail MESSAGES START ABOUT 2/3 THE WAY DOWN.

Mar 20 21:52:33 ralph-laptop fcrontab[9022]:   fcronconf=/usr/local/etc/fcron.conf
Mar 20 21:52:33 ralph-laptop fcrontab[9022]: Copied stdin to /tmp/fcr-5V22zU, about to parse file /tmp/fcr-5V22zU...
Mar 20 21:52:33 ralph-laptop fcrontab[9022]: installing file /tmp/fcr-5V22zU for user ralph
Mar 20 21:52:33 ralph-laptop fcrontab[9022]: write_buf_to_disk() : written 299/299, 1 (re)try(ies)
Mar 20 21:52:33 ralph-laptop fcronsighup[9024]:   fcronconf=/usr/local/etc/fcron.conf
Mar 20 21:52:33 ralph-laptop fcronsighup[9025]: uid: 1000, euid: 200, gid: 1000, egid: 200
Mar 20 21:52:50 ralph-laptop fcron[1372]: updating configuration from /usr/local/var/spool/fcron
Mar 20 21:52:50 ralph-laptop fcron[1372]: adding new file ralph
Mar 20 21:52:50 ralph-laptop fcron[1372]: User new.ralph Entry
Mar 20 21:52:50 ralph-laptop fcron[1372]:    dow of 3-20-2011 : 0
Mar 20 21:52:50 ralph-laptop fcron[1372]: after  mktime() : 23:53 isdst:1 ti:1300690380
Mar 20 21:52:50 ralph-laptop fcron[1372]:   cmd export DISPLAY=:0.0  &&  /home/ralph/lbtest next exec 3/20/2011 wday:0 23:53:00 (system time)
Mar 20 21:52:50 ralph-laptop fcron[1372]:    dow of 3-20-2011 : 0
Mar 20 21:52:50 ralph-laptop fcron[1372]: after  mktime() : 21:53 isdst:1 ti:1300683180
Mar 20 21:52:50 ralph-laptop fcron[1372]:   cmd export DISPLAY=:0.0&&/home/ralph/lbtest next exec 3/20/2011 wday:0 21:53:00 (system time)
Mar 20 21:52:50 ralph-laptop fcron[1372]:   from last conf: export DISPLAY=:0.0  &&  /home/ralph/lbtest next exec 3/20/2011 wday:0 23:53:00 (system time)
Mar 20 21:52:50 ralph-laptop fcron[1372]: Saving ralph...
Mar 20 21:52:50 ralph-laptop fcron[1372]: write_buf_to_disk() : written 299/299, 1 (re)try(ies)
Mar 20 21:52:50 ralph-laptop fcron[1372]:
Mar 20 21:52:50 ralph-laptop fcron[1372]: Looking for jobs to execute ...
Mar 20 21:52:50 ralph-laptop fcron[1372]: next sleep time : 10
Mar 20 21:53:00 ralph-laptop fcron[1372]:
Mar 20 21:53:00 ralph-laptop fcron[1372]: Looking for jobs to execute ...
Mar 20 21:53:00 ralph-laptop fcron[9035]: run_job(): child: mail, output to file, running in background, normal
Mar 20 21:53:00 ralph-laptop fcron[1372]:    dow of 3-20-2011 : 0
Mar 20 21:53:00 ralph-laptop fcron[1372]:    dow of 3-21-2011 : 1
Mar 20 21:53:00 ralph-laptop fcron[1372]: after  mktime() : 21:53 isdst:1 ti:1300769580
Mar 20 21:53:00 ralph-laptop fcron[1372]:    cmd: export DISPLAY=:0.0&&/home/ralph/lbtest next exec 3/21/2011 wday:1 21:53:00 (tzdiff=0, timezone=system's)
Mar 20 21:53:00 ralph-laptop fcron[1372]: next sleep time : 5
Mar 20 21:53:00 ralph-laptop fcron[9035]: Job export DISPLAY=:0.0&&/home/ralph/lbtest started for user ralph (pid 9036)
Mar 20 21:53:05 ralph-laptop fcron[1372]:
Mar 20 21:53:05 ralph-laptop fcron[1372]: Looking for jobs to execute ...
Mar 20 21:53:05 ralph-laptop fcron[1372]: Saving ralph...
Mar 20 21:53:05 ralph-laptop fcron[1372]: write_buf_to_disk() : written 304/304, 1 (re)try(ies)
Mar 20 21:53:05 ralph-laptop fcron[1372]: next sleep time : 1800

SENDMAIL MESSAGES FROM fcron ATTEMPTING TO SEND EMAIL START HERE

Mar 20 21:53:14 ralph-laptop fcron[9035]: Job export DISPLAY=:0.0&&/home/ralph/lbtest completed (mailing output)
Mar 20 21:53:14 ralph-laptop sendmail[9035]: My unqualified host name (ralph-laptop) unknown; sleeping for retry
Mar 20 21:54:15 ralph-laptop sendmail[9035]: unable to qualify my own domain name (ralph-laptop) -- using short name
Mar 20 21:54:15 ralph-laptop sendmail[9035]: p2L4sF9v009035: from=ralph, size=123, class=0, nrcpts=1, msgid=<201103210454.p2L4sF9v009035@ralph-laptop>, relay=ralph@localhost
Mar 20 21:54:17 ralph-laptop sm-mta[9060]: p2L4sGBs009060: from=<ralph@ralph-laptop>, size=400, class=0, nrcpts=1, msgid=<201103210454.p2L4sF9v009035@ralph-laptop>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Mar 20 21:54:17 ralph-laptop sendmail[9035]: p2L4sF9v009035: to=myemail@mchsi.com, ctladdr=ralph (1000/1000), delay=00:00:02, xdelay=00:00:01, mailer=relay, pri=30123, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p2L4sGBs009060 Message accepted for delivery)
Mar 20 21:54:17 ralph-laptop fcron[1372]:
Mar 20 21:54:17 ralph-laptop fcron[1372]: Looking for jobs to execute ...
Mar 20 21:54:17 ralph-laptop fcron[1372]: next sleep time : 1728
Mar 20 21:54:26 ralph-laptop sm-mta[9062]: p2L4sGBs009060: to=<myemail@mchsi.com>, ctladdr=<ralph@ralph-laptop> (1000/1000), delay=00:00:09, xdelay=00:00:09, mailer=relay, pri=120400, relay=mail.mchsi.com. [97.64.187.44], dsn=5.0.0, stat=Service unavailable
Mar 20 21:54:26 ralph-laptop sm-mta[9062]: p2L4sGBs009060: p2L4sQBs009062: DSN: Service unavailable
Mar 20 21:54:26 ralph-laptop sm-mta[9062]: p2L4sQBs009062: to=<ralph@ralph-laptop>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent


LOG MESSAGES FROM EXECUTING "sendmail [email]myemail@mchsi.com[/email]"

Mar 20 21:30:56 ralph-laptop sendmail[8617]: My unqualified host name (ralph-laptop) unknown; sleeping for retry
Mar 20 21:31:57 ralph-laptop sendmail[8617]: unable to qualify my own domain name (ralph-laptop) -- using short name
Mar 20 21:31:58 ralph-laptop sendmail[8617]: p2L4VvVU008617: from=ralph, size=13, class=0, nrcpts=1, msgid=<201103210431.p2L4VvVU008617@ralph-laptop>, relay=ralph@localhost
Mar 20 21:31:59 ralph-laptop sm-mta[8635]: p2L4VwRO008635: from=<ralph@ralph-laptop>, size=291, class=0, nrcpts=1, msgid=<201103210431.p2L4VvVU008617@ralph-laptop>, proto=ESMTP, daemon=MTA-v4, relay=localhost [127.0.0.1]
Mar 20 21:31:59 ralph-laptop sendmail[8617]: p2L4VvVU008617: to=myemail@mchsi.com, ctladdr=ralph (1000/1000), delay=00:00:02, xdelay=00:00:01, mailer=relay, pri=30013, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p2L4VwRO008635 Message accepted for delivery)
Mar 20 21:32:08 ralph-laptop sm-mta[8637]: p2L4VwRO008635: to=<myemail@mchsi.com>, ctladdr=<ralph@ralph-laptop> (1000/1000), delay=00:00:09, xdelay=00:00:09, mailer=relay, pri=120291, relay=mail.mchsi.com. [97.64.187.44], dsn=5.0.0, stat=Service unavailable
Mar 20 21:32:08 ralph-laptop sm-mta[8637]: p2L4VwRO008635: p2L4W8RO008637: DSN: Service unavailable
Mar 20 21:32:08 ralph-laptop sm-mta[8637]: p2L4W8RO008637: to=<ralph@ralph-laptop>, delay=00:00:00, xdelay=00:00:00, mailer=local, pri=30000, dsn=2.0.0, stat=Sent

---

### Post by SeijiSensei on 2011-03-21
Try installing bsd-mailx and use the command-line "mail" program it installs instead of sendmail like this:

```
echo 'This is a message' | mail -s 'My new message' someone@example.com
```

Sending mail using sendmail itself can be quite a bit more complex than using mail.  You'll still need to have sendmail (or another MTA like Postfix or Exim) running; "sudo service sendmail restart" to make sure it's up and running.

If you're trying to send mail to a remote SMTP server, you may be blocked by your ISP.  See [http://ubuntuforums.org/showthread.php?p=10584000#post10584000](http://ubuntuforums.org/showthread.php?p=10584000#post10584000) for a method to test for this.

---

### Post by Ralph L on 2011-03-23
SeijiSensei

Appreciate you getting back to me.  I ran your check for port 25.  Everything worked.  I also got sendmail to work from the cli Terminal.  I merely needed to use the -f parameter (-fmyemail@mchsi.com).  With a standard From address mail.mchsi.com accepted the message fine and I received it back in Thunderbird, my email program.  Example of sendmail under Terminal:

sendmail [email]-fmyemail@mchsi.com[/email] [email]myemail@mchsi.com[/email]
My email message.
.

However, fcron gives me no way of setting the -f parameter, or at least I can't find it.  Any ideas?

I also found that by default fcron sendmails its messages to /var/spool/mail/ralph (my computer account is ralph and my computer name is ralph-laptop) with both the From and To addresses of ralph@ralph-laptop.  I was able to read the messages fine using bsd-mailx.  If I could get Thunderbird to receive these messages, then I would have achieved my goal of having fcron messages appear in my standard email.  Do you know of anyway to have Thunderbird receive those messages?

Thanks
Ralph

---

### Post by SeijiSensei on 2011-03-23
> **Ralph L said:**
> However, fcron gives me no way of setting the -f parameter, or at least I can't find it.  Any ideas?

I don't know what fcron is.  I've only ever used "Vixie" cron, the one that comes by default in Ubuntu.  For daily backups, I write a script and create a symlink to it in /etc/cron.daily.  It then runs automatically every night.

> I also found that by default fcron sendmails its messages to /var/spool/mail/ralph (my computer account is ralph and my computer name is ralph-laptop) with both the From and To addresses of ralph@ralph-laptop.  Do you know of anyway to have Thunderbird receive those messages?

Edit (with sudo as root) the file /etc/aliases and add a line like this:

```
ralph:       ralph@somewhere.net
```

then run the command "sudo newaliases".  Now all mail sent to ralph on the local machine will be forwarded to [email]ralph@somewhere.net[/email].  You can test it from the command prompt by sending a message like:

```
echo 'This is a test' | mail -s 'forwarding test' ralph
```

You should see it appear in your mailbox in Thunderbird.

You can also test aliases by running the command:

```
sudo sendmail -bv aliasname
```

sendmail will reply with a list of the addresses to which "aliasname" points.  (Alias targets can be lists as well as individual addresses.  Run "man aliases" to learn more.)

---

### Post by Ralph L on 2011-03-23
SeijiSensei

I did as you suggested putting in the alias entry:
ralph:  [email]myemail@mchsi.com[/email]

I ran newaliases and got the error message:
WARNING: local host name (ralph-laptop) is not qualified; see cf/README: WHO AM I?
I don't know what this means, I don't know what "not qualified means, nor where to find the readme nor how to qualify ralph-laptop.  However, the alias was accepted.

I ran your test:
ralph@ralph-laptop:~$ echo 'This is a test' | mail -s 'forwarding test' ralph

My email provider "mail.mchsi.com" rejected the email with:
<<< 550 5.1.0 <ralph@ralph-laptop> sender rejected - POL107

It didn't like my From address.  I didn't see an option for changing the From address in Mail, so I ran the following under Terminal:

ralph@ralph-laptop:~$ sendmail [email]-fmyemail@mchsi.com[/email] ralph
afdkld
.

This worked fine.  The message "afdkld" showed up in my tbird Inbox.  So I have come full circle.  I am back to "how can I add the -f parameter to fcron's call to sendmail", or "how can I setup tbird to get messages with a From field of ralph@ralph-laptop".  Any thoughts?

Ralph

---

### Post by SeijiSensei on 2011-03-23
> **Ralph L said:**
> I don't know what "not qualified means, nor where to find the readme nor how to qualify ralph-laptop.  However, the alias was accepted.

I am back to "how can I add the -f parameter to fcron's call to sendmail", or "how can I setup tbird to get messages with a From field of ralph@ralph-laptop". Any thoughts?

Unqualified names have just a host part but no domain, e.g., "ralph-laptop" rather than "ralph-laptop.example.com."

We're starting to tread into some pretty complex stuff now, but I'll give it a go.

Perhaps the easiest solution is to force sendmail to use a "genericstable".  This is a map from usernames like "ralph" to fully-qualified names like [email]myemail@mchsi.com[/email].  I don't know if your sendmail has genericstable support by default, but probably it doesn't.  If not, you need to edit the file /etc/mail/sendmail.mc and use it to build a new sendmail configuration, /etc/mail/sendmail.cf.  You'll probably need to install the sendmail-cf package to do this.

With both sendmail and sendmail-cf installed, you'll need to edit the file /etc/mail/sendmail.mc.  First make a backup copy, then use "sudo nano /etc/mail/sendamil.mc" to add the lines

```

GENERICS_DOMAIN_FILE(`/etc/mail/generics-domain')dnl
FEATURE(`genericstable',`hash -o /etc/mail/genericstable.db')dnl
```

above any MAILER() statements you see at the end of the file.  Note carefully that each entry starts with the "backtick" character (left of the "1" on the top keyboard row) and ends with a single-quote (apostrophe).  If you don't get the quotes right, it won't work.

Create the generics-domain file like this:

```
sudo echo 'ralph-laptop' > /etc/mail/generics-domain
```

The entry should correspond to the result you see by running the "hostname" command.  Since sendmail has been using "@ralph-laptop", that's probably the correct entry for the generics-domain file.

Next make a backup of the file /etc/mail/sendmail.cf, then run the commands:

```
cd /etc/mail
sudo m4 sendmail.mc > sendmail.cf
```

That will create a new sendmail configuration file with the genericstable feature added.

Now to create the table itself.  Use "sudo nano /etc/mail/genericstable" to create the file and enter the following line:

```
ralph     myemail@mchsi.com
```

Finally you need to convert that file into a "hash" database.  In the /etc/mail directory, type

```
sudo makemap hash genericstable < genericstable
```

That will create a file called genericstable.db with the mapping from ralph to your actual email address.

Now sendmail should send messages from "ralph" using your actual email address as the From.  This should eliminate the need for the -f switch to sendmail as well.

---

### Post by Ralph L on 2011-04-08
I have not yet tried the "genericstable" approach to fix my problem.  I took another simpler approach using the "movemail" feature of Thunderbird.  

Movemail is designed to do exactly what I want--move mail from my local mailbox (/var/mail/ralph (or root)) to my TB Inbox.  (Note:  Sendmail by default sends mail to /var/mail/username.) However, TB has a bug (bug #299261) in it that prevents it from doing exactly what I want. TB will only movemail into the Inbox of a new account (.../profilename/Mail/localhost-7).  And it will not automatically periodically check for new mail in this account.  It must be done manually by selecting the Movemail account Inbox and clicking the "Get Mail" icon.  I tried to get around this by going to TB>Edit>Account Settings>Server Settings(for the Movemail account)>Local Directory>Browse and setting it to my Local Folders/Inbox.  It took the setting, but immediately went back to "localhost/Inbox".  I also tried replacing "localhost/Inbox" and "localhost/Inbox.msf" with symbolic links to "Local Folders/Inbox".  It kind of worked, but caused TB to continually rebuild "localhost/Inbox.msf", so I gave up.

See [http://ubuntuforums.org/showthread.php?t=1718795](http://ubuntuforums.org/showthread.php?t=1718795) for how to set up movemail in Thunderbird.

However, it is not super troublesome to have to click on the "Movemail_account>Inbox and Get Mail once a day to see if my backups have run correctly.  For now I am going with that solution.  I may come back and set up "genericstable" if I get time.

Note:  From info I gleaned while web surfing, I think that Evolution has some feature akin to "movemail" and that it actually works.  I would change to Evolution except it doesn't have the features of Thunderbird add-ons ([http://nic-nac-project.de/~kaosmos/mboximport-en.html](http://nic-nac-project.de/~kaosmos/mboximport-en.html) ) for importing and exporting email, etc to MS Mail.

NOTE 2: In order to get sendmail to work without getting a message about my computer name (ralph-laptop) being "not fully qualified" I edited the second line of /etc/hosts to be "127.0.1.1 ralph-laptop ralph-laptop.local" (no quotes). This added the alias "ralph-laptop.local. I guess this "qualified" the name ralph-laptop. Anyway I no longer get the error message and sendmail sends the message immediately rather than waiting a minute and doing a retry. Hope this information is useful to somebody.

Ralph

---

