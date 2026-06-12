---
title: "Need help on evolution - constantly &quot;fetching mail&quot; at 0%"
date: 2010-11-23
forum: General Help
---

### Post by Merlin70 on 2010-11-23
Hello, I'm rather new to ubuntu (10.10) but I like it a lot already.
I have though a problem with evolution mail and hope to get some advice here, or some advice where to get support.

I'm using evolution for a few POP-email-accounts, and most things work fine (sending and receiving email, sorting into folders etc).

However, evolution permanently displays a row reading "fetching mail" at the bottom of the window, most times the row is splitted into two or three "fetching mail" - probably representing activity for seperate email accounts though it never tells which one is which.
Strange enough this "fetching" hardly ever stops, evolution remains "fetching" for hours(!) at "0% complete", even when all new mails (usually just a hand full per day) already have been downloaded and displayed.
For several reasons I leave all my mail on the server as well, this means there are lots of mail on the server which I downloaded, read and deleted (locally!) in evolution. 
I GUESS that evolution keeps checking and downloading old mails left on the server just to dispose them instantly again when the program discovers that these mails already have been read and deleted locally.
Is that possible? Any other explanation?

The problem is that I'm paying for internet by "megabyte" (no flat-rate), and apparently evolution DOES download lots of data that I never get to see, i.e. without any use but at a cost.....


Can anybody explain whats happening?

Is there any option in evolution to make it just check and download the latest, never before downloaded mails, and then stop "fetching"?

Is there any option in evolution to check on account at a time? (clicking "send/receive" button makes evolution check all accounts as far as I understand).

Is there a possibility to just send mails in the outbox, without, at the same time, checking mail (I only have the combined "send/receive" button.


Sorry for this long description, I hope someone can give advice?

Thanks from Sweden

---

### Post by plucky on 2010-11-23
Welcome to the Forum.


> I'm using evolution for a few POP-email-accounts, and most things work fine 

When you first set up your accounts in Evolution,it will try to download all the messages from the server.
This is because to Evolution all the messages are unread.
When you delete or read a message it will remember that it is deleted or read and not try to download it again.

You could open **Edit > Preferences** and disable all accounts and just enable one account at a time and see which one is staying at 0%.I think it is the one with the most emails being downloaded and hasn't finished.

> I GUESS that evolution keeps checking and downloading old mails left on the server just to dispose them instantly again when the program discovers that these mails already have been read and deleted locally.
Is that possible? Any other explanation?



The default time is set to 10 minutes to check for new mail.You could extend this to stop Evolution going to the server too often.I guess it has to do a sync between the local mailbox and the mailbox on the server.

It only then downloads any unread emails.

> Is there any option in evolution to make it just check and download the latest, never before downloaded mails, and then stop "fetching"?


That is the default.

> Is there any option in evolution to check on account at a time? (clicking "send/receive" button makes evolution check all accounts as far as I understand).


You can vary the times that Evolution goes to the server for each email account.Open **Edit > Preferences > Select Account > Edit > Receiving Options** and set the time.

> Is there a possibility to just send mails in the outbox, without, at the same time, checking mail (I only have the combined "send/receive" button.

No


Hope this helps.

Good Luck

---

