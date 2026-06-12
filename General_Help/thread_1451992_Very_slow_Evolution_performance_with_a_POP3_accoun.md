---
title: "Very slow Evolution performance with a POP3 account"
date: 2010-04-11
forum: General Help
---

### Post by brianmc on 2010-04-11
It's likely coming on for a year since I first seriously tried to switch to Ubuntu. I now find myself very rarely booting into Windows XP, and all the apps I need to use have free replacements.

However, after porting about 15-20 years worth of email from Outlook (via Thunderbird) into Evolution, I'm finding Evo's performance has gone down the toilet.

It was snappy to start with, but over time has got slower. I regularly get long waits as it displays notes that it is retrieving message number <whatever>.

I'm using POP3/SMTP for most email (I've a low-usage IMAP account with gmx.com too), but it seems like some sort of issue where I'd want to optimise or "defragment" my local mail store.

Has anyone any ideas or suggestions on this?

My ~/.evolution/mail folder contains about 2.5Gb if that's any help.

This is with 9.10 Ubuntu; I have done some basic tuning on the setup, but not a lot.

---

### Post by brianmc on 2010-04-11
yuvi, you're reported for spamming.

Have a nice day in the killfile.

---

### Post by vitaraq on 2010-06-17
I have installed 10.04 and i am finding evo very slow especially the start up.

---

### Post by brianmc on 2010-06-17
> **vitaraq said:**
> I have installed 10.04 and i am finding evo very slow especially the start up.

Sounds a similar problem to me. Can you document the way you're retrieving/accessing email, the size of the local or remote mailstore, and - basically - as much data as possible?

I know I moaned about this quite some time ago. I'll offer what advice I can, based on my own efforts to resolve the issue; but, it is an issue of hoping developers would take that on as sort-of wish-list stuff.

First off, you'll have loads, and loads of deleted messages in your various folders that you never see. User Folder->Expunge (Ctrl-E) liberally to clear that out.

Then, investigate setting up mail handling rules to archive stuff into long-term folders. There is a trade-off between having a small amount in a folder, and doing these tasks at startup.

Regrettably, I'd still say that Evo is a bit slower than the over-expensive Microsoft products it tries to compete with. But, that's typed from a 1Gb 6+ year-old machine. Depending on your usage, I'd say it is perfectly acceptable to have Evo as a program you wait for on login, and keep running. You're saving a small fortune in comparison to Outlook licensing, your mail is in a published, documented format that ain't going to vanish; just quietly convert people to trying it before they throw a two-year-old laptop in the trash to get Win7.

---

