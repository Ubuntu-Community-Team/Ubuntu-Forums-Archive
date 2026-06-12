---
title: "Evolution Receiving Messages to where?"
date: 2011-01-12
forum: General Help
---

### Post by juantogo on 2011-01-12
Hi all,

I got Evolution 2.28.3 configured and working fine for a while, but today, actually for the last 3 or I suspect, when I click on Send/Receive, Evolution brings up a window, connects to my Gmail and Yahoo Plus accounts just fine.  I see it receiving messages, as many as 75 at a time, but when I look in my inbox, no new messages.  No new messages in Junk either.

Where could they be going.  I see the message counter clicking off the messages as if downloading but they're not here...

Anybody else have this problem?  When I go to yahoo.com, login and check the mail, I see message, old and newer ones, sitting on the server.

Thnks in Advance,

---

### Post by Tamlynmac on 2011-01-12
Just a quick thought.

Have you checked your Evolution trash? I'm  wondering if you have any filters enabled (evolution/edit/message  filters) filtering incoming messages and automatically sending them to  the trash. Check trash immediately after downloading messages. You may  have setup empty trash on exit, which would do just that if you close  evolution and re-open it.

If you have any message filters, they may be setup incorrectly. Which  may send wanted e-mails to the trash. If this is the case, post a copy  of your message filter (edit) and what you're trying to accomplish.

* You evolution setup maybe leaving messages on the server which would  explain why you find them when checking the server directly.
(evolution/edit/edit account/receiving options tab/message storage section/leave messages on server)

Good Luck & hope this helps.

---

### Post by juantogo on 2011-01-12
Thanks. 

I just check the trash and its full, but not of new messages.  No filters enabled that I know of...and nothing is going into Junk even tho I have marked some previous as Junk.

UPDATE:
Yesterday I created new partitions etc and new users etc.
Then I rebooted back to my old login partition on sda1 (WinXP), and exported Evolution settings.
I rebooted, opened Evolution, imported settings and it found the mail servers at gmail and yahoo again and I received mail...but no new mail appears.
If I r-click on the Inbox Properties, it shows 325 unread, which I haven't, and 2354 Total Messages. When I get new mail, by clicking on send/recv the mail total goes up accordingly to the number downloaded...BUT, the unread stays the same and no new messages appear in the inbox....?
Wierd...
Permissions on folders is all me and group is adm.
Still searching...
UPDATE:  
sent myself mail and it appears on the Yahoo server.
No error message on Evo client.

---

### Post by juantogo on 2011-01-13
> **juantogo said:**
> Thanks. 

I just check the trash and its full, but not of new messages.  No filters enabled that I know of...and nothing is going into Junk even tho I have marked some previous as Junk.

UPDATE:
Yesterday I created new partitions etc and new users etc.
Then I rebooted back to my old login partition on sda1 (WinXP), and exported Evolution settings.
I rebooted, opened Evolution, imported settings and it found the mail servers at gmail and yahoo again and I received mail...but no new mail appears.
If I r-click on the Inbox Properties, it shows 325 unread, which I haven't, and 2354 Total Messages. When I get new mail, by clicking on send/recv the mail total goes up accordingly to the number downloaded...BUT, the unread stays the same and no new messages appear in the inbox....?
Wierd...
Permissions on folders is all me and group is adm.
Still searching...
UPDATE:  
sent myself mail and it appears on the Yahoo server.
No error message on Evo client.

UPdate: moved .evolution directory, reinstalled. Now all mail goes to junk. Better than before.  Previous issue not resolved really but moving forward now...

---

### Post by Tamlynmac on 2011-01-13
> juantogo

Have you tried turning off your junk filter?
[edit/preferences/mail preferences/junk tab]

It's odd that all incoming e-mail is being identified as junk. Especially, if you have no message filters. You can select all the e-mails that aren't junk and right click on them marking them as not junk. The next time you get e-mail, those senders that are marked as not junk should then arrive in your in-box.

Hopefully, someone else may have experienced this issue and will chime in.

Good Luck

---

