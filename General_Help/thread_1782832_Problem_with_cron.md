---
title: "Problem with cron"
date: 2011-06-15
forum: General Help
---

### Post by formula on 2011-06-15
Hi

I've setup a cron job to run every day at 13:00. When I run it manually it works but with the cron it doesn't

this is the log:
```

Jun 14 13:00:01 testserver CRON[5662]: (scialom) CMD (lynx http://www.something.com/sms_reminder.php # JOB_ID_4)
Jun 14 13:00:02 testserver CRON[5661]: (CRON) info (No MTA installed, discarding output)
Jun 14 13:00:08 testserver dhclient: DHCPREQUEST of 10.0.0.6 on eth0 to 10.0.0.138 port 67
Jun 14 13:01:14 testserver dhclient: last message repeated 4 times

```

any idea why?

thanks!

---

### Post by DaithiF on 2011-06-15
Hi, capture the output of the job to a file so that you can see what errors are reported.  there are a variety of reasons why jobs may fail under cron, so rather than guess which particular ones are an issue in your case, lets find the errors first.

append something like this to your job definition in cron to capture stdout/stderr output to a file:

**> /path/to/file 2>&1**

---

### Post by gmargo on 2011-06-15
> **formula said:**
> 
```

Jun 14 13:00:01 testserver CRON[5662]: (scialom) CMD (lynx http://www.something.com/sms_reminder.php # JOB_ID_4)
Jun 14 13:00:02 testserver CRON[5661]: (CRON) info (No MTA installed, discarding output)

```

It is working. The cron daemon ran lynx and emailed the output to you.

However you do not have an [MTA]("http://en.wikipedia.org/wiki/Message_transfer_agent") installed, so this information gets tossed.

Please install a Message Transfer Agent (aka Mail Server) such as postfix or exim4.  Then you will be the proud recipient of email from the cron daemon.

Even if you redirect the output of your cron command(s), you should always have an MTA installed, since cron will email any error codes or messages to you.  That is information you don't want to miss.

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
[http://en.wikipedia.org/wiki/Message_transfer_agent](http://en.wikipedia.org/wiki/Message_transfer_agent)

---

