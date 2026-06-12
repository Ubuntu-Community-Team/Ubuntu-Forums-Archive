---
title: "Evolution shows unread messages but there are none"
date: 2011-11-07
forum: General Help
---

### Post by gofurygo on 2011-11-07
Hello all,

Im using Ubuntu 11.04 with evolution 2.32.2 and an imap mail account.

Recently I experienced some strange behaviour. In the subfolders "spam" and "trash" are no emails visible at all. Nevertheless, on the folder-tree (left hand side) it shows SPAM (3) and TRASH (1) unread messages... if I click on the folders, it shows "no emails in this..."

I already went to home/.local/share/evolution/mail/imap/ and deleted the journal, .ev-store-summary, and cmeta files in order for evolution to re-create them on start-up... but it didnt work. It still shows messages although there are none...

Right-click on eg. SPAM and properties shows: 3 unread messages, 0 messages total :-D

If I log on to this account online, it also shows no messages. So I reckon it must be an evolution problem...

Anybody got an idea how to fix this?

---

### Post by dcstar on 2011-11-08
> **gofurygo said:**
> Hello all,

Im using Ubuntu 11.04 with evolution 2.32.2 and an imap mail account.

Recently I experienced some strange behaviour. In the subfolders "spam" and "trash" are no emails visible at all. Nevertheless, on the folder-tree (left hand side) it shows SPAM (3) and TRASH (1) unread messages... if I click on the folders, it shows "no emails in this..."

I already went to home/.local/share/evolution/mail/imap/ and deleted the journal, .ev-store-summary, and cmeta files in order for evolution to re-create them on start-up... but it didnt work. It still shows messages although there are none...

Right-click on eg. SPAM and properties shows: 3 unread messages, 0 messages total :-D

If I log on to this account online, it also shows no messages. So I reckon it must be an evolution problem...

Anybody got an idea how to fix this?

So what happens when **you** mark them as Read?

---

### Post by gofurygo on 2011-11-08
> So what happens when **you** mark them as Read? 

A small window opens, "Do you want to mark all messages as read?" I confirm with yes, then nothing happens, it still shows unread messages in both folders...

---

### Post by gofurygo on 2011-11-08
Emm... I "fixed" it... I moved 1 message from inbox to SPAM, another one to TRASH... suddenly Evolution updated the number of unread mails in those 2 folders. I deleted/moved them, and everything is normal again...:confused:

Very strange...  thanks for your help anyway ;-)

---

### Post by OneidaLake on 2012-01-11
Hey, thanks for the info.  This has been causing me grief for a few days.  It started when I began using a second device to check IMAP messages.  I sent myself a test message, put it in the "offending" folder and all was good.

---

