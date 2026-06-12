---
title: "Thunderbird 3 - How to re-index?"
date: 2009-12-17
forum: General Help
---

### Post by MidBSD on 2009-12-17
During the install of Thunderbird 3 I had to restart because it seemed to stop indexing after going through only about 1/3 of my emails.

I should mention it automatically detected my emails from my Thunderbird 2 install which I had just uninstalled.

Naturally, when I now do a search, I won't get a full resultset.

How can I re-index my emails or how can I even re-initialise the install procedure so that it will re-index all the emails?

---

### Post by MidBSD on 2009-12-17
I've been Googling and looking through all Thunderbird's menus and no sooner do I post the question than I find the answer.

Go to File -> Offline -> Download/Sync Now

This will finish downloading any emails that may not have made it down in the first attempt.

Whilst Googling around I could see other people trying to simply re-index what they already had downloaded - unfortunately this doesn't solve that problem :(

---

### Post by MidBSD on 2009-12-17
It appears I'm confounding downloading and syncing of email with indexing.

Whilst download/sync does download the email - it doesn't appear to index them as they did during the migration from TB2 -> TB3.

As such, I still can't do a complete search throughout my emails.

Anyone any other ideas?

---

### Post by qva5 on 2010-01-02
> **MidBSD said:**
> It appears I'm confounding downloading and syncing of email with indexing.

Whilst download/sync does download the email - it doesn't appear to index them as they did during the migration from TB2 -> TB3.

As such, I still can't do a complete search throughout my emails.

Anyone any other ideas?

Try to delete GLODA file, which should force TB3 to reindex all messages at restart.

> The gloda database is a SQLite database named "global-messages-db.sqlite" and can currently be found in the user's profile directory.Just remeber to backup your data in case something would go wrong.

---

### Post by leobard on 2010-08-06
works!

> **qva5 said:**
> Try to delete GLODA file, which should force TB3 to reindex all messages at restart.

The gloda database is a SQLite database named "global-messages-db.sqlite" and can currently be found in the user's profile directory. 

Just remeber to backup your data in case something would go wrong.

I had the problem that thunderbird's fulltext search stopped working. Only the search for emailaddresses was still working in global search.
I updated from 3.0.6 to 3.1.2, this did not help but also did not harm. Then I made a MozBackup and deleted global-messages-db.sqlite. TB3.1 started and began indexing fully automatic, I could see the file growing bigger again.

search worked again.

so - this thread is helpful!!! thanks.

---

### Post by mwildam on 2010-10-18
I somehow seem to have a similar problem with my IMAP account. But I do not really want to start reindexing from scratch as my mailbox is very big (emails since 2004 - of course not all in my inbox ;-) ).

Is there an option to re-index just particular folders?

---

### Post by qva5 on 2010-11-02
> **mwildam said:**
> I somehow seem to have a similar problem with my IMAP account. But I do not really want to start reindexing from scratch as my mailbox is very big (emails since 2004 - of course not all in my inbox ;-) ).

Is there an option to re-index just particular folders?

Hard to tell. 
But with such specific question I  would try to find an answer on **mozilla/thunderbird** forum.

---

### Post by grumpypants on 2012-01-24
I have been wondering this too. I just discovered a round-about solution using Thunderbird 9 and Thunderbird Conversations ([https://addons.mozilla.org/en-US/thunderbird/addon/gmail-conversation-view](https://addons.mozilla.org/en-US/thunderbird/addon/gmail-conversation-view)). When you first install Thunderbird Conversations it re-indexes your messages. It also happily provides a way to repeat this on demand.

Tools -> Add-Ons -> Extensions -> Thunderbird Conversations -> Preferences -> Start the setup assistant -> Apply changes

If you click Review changes before clicking Apply changes, you'll see that the following are checked:

[LIST]
[*]Make sure Global Search and Indexer is enabled.
[*]Re-index messages containing attachments as well as all Mozilla bugmail.
[/LIST]
After doing so you can monitor progress with Tools -> Activity Manager

---

### Post by BC59 on 2012-01-24
> **grumpypants said:**
> I have been wondering this too. I just discovered a round-about solution using Thunderbird 9 and Thunderbird Conversations ([https://addons.mozilla.org/en-US/thunderbird/addon/gmail-conversation-view](https://addons.mozilla.org/en-US/thunderbird/addon/gmail-conversation-view)). When you first install Thunderbird Conversations it re-indexes your messages. It also happily provides a way to repeat this on demand.

Tools -> Add-Ons -> Extensions -> Thunderbird Conversations -> Preferences -> Start the setup assistant -> Apply changes

If you click Review changes before clicking Apply changes, you'll see that the following are checked:

[LIST]
[*]Make sure Global Search and Indexer is enabled.
[*]Re-index messages containing attachments as well as all Mozilla bugmail.
[/LIST]
After doing so you can monitor progress with Tools -> Activity Manager

Should be a could idea to post it as new thread on Tutorials & Tips. In this old thread is going to pass unnoticed.

---

### Post by grumpypants on 2012-01-24
> **BC59 said:**
> Should be a could idea to post it as new thread on Tutorials & Tips. In this old thread is going to pass unnoticed.

OK, done. (Though this old thread certainly has some visibility -- I found it because it is still the first hit on a DuckDuckGo search for "thunderbird re-index"! [https://duckduckgo.com/?q=thunderbird+re-index](https://duckduckgo.com/?q=thunderbird+re-index))

---

### Post by oldos2er on 2012-01-24
Closed, necromancy.

---

