---
title: "If user has own crontab, results in accumulation of root CRON processes"
date: 2010-02-05
forum: General Help
---

### Post by narnie on 2010-02-05
Hello,

I seem to be having a problem with accumulation of root CRON jobs occuring when I have a user's cron job(s) running.

Here is an example of a user's crontab file:

```
*/1	*	*	*	*	echo "hello" > /dev/null
```

```
ps aux|grep CRON
root     14333  0.0  0.0  91236  2172 ?        S    21:44   0:00 CRON
root     14334  0.0  0.0  91244  1284 ?        S    21:44   0:00 CRON
root     14366  0.0  0.0  91236  2172 ?        S    21:45   0:00 CRON
root     14367  0.0  0.0  91244  1284 ?        S    21:45   0:00 CRON
root     14375  0.0  0.0  91236  2172 ?        S    21:46   0:00 CRON
root     14377  0.0  0.0  91244  1284 ?        S    21:46   0:00 CRON
root     14386  0.0  0.0  91236  2172 ?        S    21:47   0:00 CRON
root     14387  0.0  0.0  91244  1284 ?        S    21:47   0:00 CRON
root     14396  0.0  0.0  91236  2172 ?        S    21:48   0:00 CRON
root     14397  0.0  0.0  91244  1284 ?        S    21:48   0:00 CRON
root     14423  0.0  0.0  91236  2172 ?        S    21:49   0:00 CRON
root     14424  0.0  0.0  91244  1284 ?        S    21:49   0:00 CRON
root     14471  0.0  0.0  91236  2172 ?        S    21:50   0:00 CRON
root     14472  0.0  0.0  91244  1284 ?        S    21:50   0:00 CRON
root     14482  0.0  0.0  91236  2172 ?        S    21:51   0:00 CRON
root     14483  0.0  0.0  91244  1284 ?        S    21:51   0:00 CRON
root     14693  0.0  0.0  91236  2172 ?        S    22:04   0:00 CRON
root     14694  0.0  0.0  91244  1284 ?        S    22:04   0:00 CRON
root     14727  0.0  0.0  91236  2172 ?        S    22:07   0:00 CRON
root     14728  0.0  0.0  91240  1252 ?        S    22:07   0:00 CRON
root     14736  0.0  0.0  91236  2172 ?        S    22:08   0:00 CRON
root     14737  0.0  0.0  91240  1252 ?        S    22:08   0:00 CRON
root     14746  0.0  0.0  91236  2172 ?        S    22:09   0:00 CRON
root     14747  0.0  0.0  91240  1252 ?        S    22:09   0:00 CRON
root     15129  0.0  0.0  91236  2172 ?        S    22:10   0:00 CRON
root     15130  0.0  0.0  91240  1252 ?        S    22:10   0:00 CRON
root     15166  0.0  0.0  91236  2172 ?        S    22:11   0:00 CRON
root     15167  0.0  0.0  91240  1252 ?        S    22:11   0:00 CRON
root     15178  0.0  0.0  91236  2172 ?        S    22:12   0:00 CRON
root     15179  0.0  0.0  91240  1252 ?        S    22:12   0:00 CRON
root     15267  0.0  0.0  91236  2172 ?        S    22:13   0:00 CRON
root     15268  0.0  0.0  91240  1252 ?        S    22:13   0:00 CRON
root     15276  0.0  0.0  91236  2172 ?        S    22:14   0:00 CRON
root     15277  0.0  0.0  91240  1252 ?        S    22:14   0:00 CRON
```

Each of the CRONs have to do with running the user's crontab file as evidenced by from the /var/log/syslog:

```
Feb  5 22:14:01 toshiba-laptop CRON[15278]: (woodnt) CMD (echo "hello" > /dev/null)
```

When I delete the offending crontab, of course, all the root CRON jobs 

I can find nothing to make them go away short of a script killing the processes by IDs.

Any idea how/why this is happening and how to stop it?

Yours,
Narnie

---

### Post by narnie on 2010-02-05
BTW,

It seems root nor the user are getting emails on the crontab jobs being run.

Yours,
Narnie

---

### Post by dcstar on 2010-02-06
> **narnie said:**
> BTW,

It seems root nor the user are getting emails on the crontab jobs being run.


They only get e-mails for **failed** cron jobs.

That command runs correctly on my 9.04 system without any leftover processes, since you have not specified what you are using then that is all I can offer.

---

### Post by narnie on 2010-02-06
> **dcstar said:**
> They only get e-mails for **failed** cron jobs.

That command runs correctly on my 9.04 system without any leftover processes, since you have not specified what you are using then that is all I can offer.

According to the info I read, ubuntu is set up for running cron at log level 1, which will send an email that the process was run or when there is an error.

I have run it on another computer without any problems, too.

I'm running 9.10

I have deleted the mailx program to see if it is hanging on the sendmail.
It tries to send the mail, but then there is no process and it seems to hang there.

This is a ps auxf with bsd-mailx (which depends postfix):

```
root     14693  0.0  0.0  91236  1660 ?        S    Feb05   0:00  \_ CRON
root     14694  0.0  0.0  91244  1160 ?        S    Feb05   0:00  |   \_ CRON
woodnt   14696  0.0  0.0  50152  2800 ?        S    Feb05   0:00  |       \_ /usr/sbin/sendmail -i -FCronDaemon -oem woodnt
```

This is with mailx/postfix unintalled:

```
root     31543  0.0  0.0  91236  2196 ?        S    17:47   0:00  \_ CRON
root     31544  0.0  0.0  91240  1272 ?        S    17:47   0:00      \_ CRON
woodnt   31545  0.0  0.0      0     0 ?        Zs   17:47   0:00          \_
```

Hence my belief that it has to do with mailing and cron jobs.

Any other ideas from anyone?

Narnie

---

