---
title: "setup system mails"
date: 2012-02-07
forum: General Help
---

### Post by Martur on 2012-02-07
Hi.

I'd like to receive root emails containing system alerts but so far /var/mail/ is empty and no mails are delivered.
I suppose there is no mail delivery system installed and so I installed postfix. Problem is that I do not know what options need to be setup so that mails will be delivered locally.

System:Ubuntu 11.10

Edit: I do not have a strong need for postfix and would be happy with any MTA that allows me to 1. receive root notifications at all & 2. is capable of forwarding all local root mail to a "real" mail address.

---

### Post by btindie on 2012-02-07
See "man aliases". After editing /etc/aliases you need to run "sudo newaliases" to update the db.

You can have root email forwarded to another local account or to another domain.

---

### Post by Martur on 2012-02-07
I know that I need to setup aliases as soon as the MTA works. 
Problem is to setup the MTA so that it delivers emails to /var/mail/root
Right now the folder /var/mail is empty

---

### Post by btindie on 2012-02-07
By default emails are delivered to ~/mbox which is a single file. Use the mail command to read them. You might want to also install heirloom-mailx. It's also possible to get Evolution to read mbox style files. There's another format called [Maildir]("https://help.ubuntu.com/community/PostfixBasicSetupHowto#Setting_Postfix_Support_for_Maildir-style_Mailboxes") where it stores them in individual files.

If you want them to go to a different location, such as /var/spool/mail, then you'll need to reconfigure it. There's a few examples [here]("https://help.ubuntu.com/community/Postfix") for virtual systems.

Depending on how you want to do it you'll need to set either both or one of [home_mailbox]("http://www.postfix.org/postconf.5.html#home_mailbox") or [mail_spool_directory]("http://www.postfix.org/postconf.5.html#mail_spool_directory").

---

