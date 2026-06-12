---
title: "Making backup of IMAP email accounts"
date: 2012-09-03
forum: General Help
---

### Post by lseg on 2012-09-03
Hi you all,

I am using several email accounts on the internet, mainly from Fastmail and gmail. 

I would like to avoid loosing mails from these accounts. So I setup Thunderbird on my Linux PC to download all mails.

But I realized that this is not really a backup, Thunderbird is synchronizing with the imap server (even not sure if it downloaded all attachments). So if I (or the webservice) accidentally deletes my mails, Thunderbird will synchronize and also delete everything.

So this is my problem: I would like to backup everything from the imap server. How do I do that ?

Can I setup Thunderbird, not to delete things.
Should I use another tool to backup all IMAP servers.
I would prefer the backup to maybe store the mails in eml format, seems more incremental than 1 big x Gb file.

I am open for suggestions. Of course it needs to work in an automated way.

kind regards,

Luc

---

### Post by opensshd on 2012-09-03
I have no idea, but saw getmail4 in the repos'.

[https://launchpad.net/ubuntu/+source/getmail4](https://launchpad.net/ubuntu/+source/getmail4)

Is that what you're looking for?

---

### Post by lseg on 2012-09-03
This getmail4 could be a possibility. 

But I would like to know how to set it up for IMAP that it would only download new messages, and not delete the message which were deleted in the webmail account.

If I can do the same thing with Thunderbird, why would I take getmail4 ?

Both Thunderbrid and getmail4 are dumping all mails in 1 big file (which is a minus). An I believe both will standard us synchronisation of the imap account instead of backup.

kind regards,

Luc

---

### Post by Zill on 2012-09-03
lseg:  Could you archive via Thunderbird's "Local Folders"? ...
[LIST]
[*][Archiving your e-mail]("http://kb.mozillazine.org/Archiving_your_e-mail")
[*][Local Folders]("http://kb.mozillazine.org/Local_Folders")
[/LIST]

---

### Post by OrangeCrate on 2012-09-03
I suppose you could reinstall the accounts in Thunderbird using POP (change your preference in Gmail too) rather that IMAP, and that would download all of your emails to Thunderbird, then backup from there. Simply drag the .thunderbird folder (hidden file) to a stick, and you're all set. 

Personally, I couldn't do that - I'd be buried by the avalance from Gmail, but if you don't have a lot of stuff, it could be a viable option to look at.

---

### Post by newb85 on 2012-09-03
I would definitely NOT switch your accounts to POP3.

There are several CLI applications for creating archives of your emails.  The only one I have experience with is archivemail (available in the repositories).  I know the archives it creates can be opened by Evolution, and probably by Thunderbird, too.

You could use a shell script and cron for routine backups.

---

### Post by lseg on 2012-09-04
The problem is:
I dont want to archive, I want to backup my mails, in the event something goes wrong with fastmail or gmail.

I always use the webservice, and I would like to keep all my mails on the IMAP server. I just would like to have a local backup of my mails on my home PC.

An archive would mean, I would have to move my mails locally. I dont want to move them, I want to copy/backup them locally.

kind regards,

Luc

---

