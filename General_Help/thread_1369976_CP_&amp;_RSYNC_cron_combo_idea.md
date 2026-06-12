---
title: "CP &amp; RSYNC cron combo idea"
date: 2010-01-01
forum: General Help
---

### Post by Al Grant on 2010-01-01
Hi,

I have a Linux based NAS, which unfortunately appears to be a bit underpowered, heres why I say that:

5 PC's backup to the NAS on a weekly full with hourly incrementals 7 days a week between 7am and 6pm (2 week retention policy). There is no problem with that.

Where there is a problem is getting that data off the NAS to the USB attached storage for off site (2 disks swapped weekly). The built in RSYNC via the web gui takes about 3 days to sync to USB after the weekly full (Sun night)- 100% CPU. The fulls are about 20-40Gb each.

I was thinking about one of two ways around this:

1. using cron and cp copy the weekly fulls to the USB storage, then use nightly rsyncs to keep everything else up to date. I am assuming here that rsync wont recopy the stuff copied with cp?

The logic of the cp cron job would need to be something like:
*delete stuff created over 8 days ago
*copy all files in backup dir recursively that dont already exist (should only be full backups)
*run a rsync for cleanup

2. use rsync exclusively, but schedule it to only run it outside of business hours, ie let it run from 7pm -5am and kill it at 5am. Over the course of the week it should catch up?

Any thoughts on these two methods? I realise that option 1 gives you no assurance that the copy completed successfully.

Cheers

-Al

---

### Post by gsmanners on 2010-01-01
Is it USB 1 or USB 2? That would be the problem, I think. USB 1 goes pretty slow.

---

