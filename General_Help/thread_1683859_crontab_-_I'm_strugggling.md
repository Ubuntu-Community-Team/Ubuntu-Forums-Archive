---
title: "crontab - I'm strugggling"
date: 2011-02-08
forum: General Help
---

### Post by bill-lancaster on 2011-02-08
This line in my crontab

00 11 * * * /usr/bin/get_iplayer --pvr-queue --type=radio --pid=b00y8tzq

ran but produced no result (its supposed to record a BBC programme)

syslog shows:-

Feb  8 12:09:01 bill-Vostro-200 CRON[3937]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb  8 12:09:01 bill-Vostro-200 CRON[3935]: (CRON) info (No MTA installed, discarding output)
Feb  8 12:09:18 bill-Vostro-200 kernel: [14067.084553] usb 1-6: new high speed USB device using ehci_hcd and address 4
Feb  8 12:09:18 bill-Vostro-200 kernel: [14067.231356] scsi5 : usb-storage 1-6:1.0
Feb  8 12:09:19 bill-Vostro-200 kernel: [14068.231640] scsi 5:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
Feb  8 12:09:19 bill-Vostro-200 kernel: [14068.234552] sd 5:0:0:0: Attached scsi generic sg2 type 0
Feb  8 12:09:19 bill-Vostro-200 kernel: [14068.240958] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Feb  8 12:09:21 bill-Vostro-200 kernel: [14069.486431] hub 1-0:1.0: port 6 disabled by hub (EMI?), re-enabling...
Feb  8 12:09:21 bill-Vostro-200 kernel: [14069.486440] usb 1-6: USB disconnect, address 4
Feb  8 12:09:21 bill-Vostro-200 kernel: [14069.752032] usb 1-6: new high speed USB device using ehci_hcd and address 5
Feb  8 12:09:21 bill-Vostro-200 kernel: [14069.900206] scsi6 : usb-storage 1-6:1.0
Feb  8 12:09:22 bill-Vostro-200 kernel: [14070.903175] scsi 6:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
Feb  8 12:09:22 bill-Vostro-200 kernel: [14070.904118] sd 6:0:0:0: Attached scsi generic sg2 type 0
Feb  8 12:09:22 bill-Vostro-200 kernel: [14070.914685] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Feb  8 12:17:01 bill-Vostro-200 CRON[4073]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  8 12:39:01 bill-Vostro-200 CRON[4343]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Feb  8 12:39:01 bill-Vostro-200 CRON[4341]: (CRON) info (No MTA installed, discarding output)
Feb  8 12:49:42 bill-Vostro-200 crontab[4485]: (bill) BEGIN EDIT (bill)

There's no event for 12:00!

What is MTA?

Can anyone help?

---

### Post by bill-lancaster on 2011-02-08
Hadn't thought of that!
I'll try it
thanks
Bill

---

### Post by gmargo on 2011-02-08
"MTA" is [Message Transfer Agent]("http://en.wikipedia.org/wiki/Message_transfer_agent"), which is a mail server program like postfix or exim4.

The cron daemon is helpfully trying to email to you the output (stdout and stderr) of the cron job.  Install an MTA and then you'll discover the error.

---

### Post by dcstar on 2011-02-08
> **Major_Bloodnok said:**
> Is 'get-iplayer' a perl script, then you may need to tell crontab to run perl.
.........

And if it is a Graphical app then there is no setting of the "DISPLAY=" output, so it will not run.

---

### Post by wojox on 2011-02-08
> **bill-lancaster said:**
> 

00 11 * * * /usr/bin/get_iplayer --pvr-queue --type=radio --pid=b00y8tzq

There's no event for 12:00!


You set it to run at 11:00 am everyday.

---

