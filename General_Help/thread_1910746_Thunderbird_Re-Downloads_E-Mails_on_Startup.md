---
title: "Thunderbird Re-Downloads E-Mails on Startup"
date: 2012-01-17
forum: General Help
---

### Post by SillySod on 2012-01-17
I've just started using Thunderbird, I've now got it configured to how I want it but a curious thing happens every time I start Thunderbird: it appears to re-download thousands of e-mail messages which it has already downloaded and stored locally.  In the present instance, it has been downloading/indexing/synchronising continuously for the last 45 minutes since I re-started it, with no end in sight.  I need it to stop doing this as it is slowing down my computer and my web access, and if I was using Thunderbird with mobile broadband (which I will want to do in a couple of days' time) it will use up all my data quota and end up costing me money for no good reason.

I have several mail accounts set up in Thunderbird, they are all IMAP and I have subscribed to all the folders in my accounts so Thunderbird accesses them all.  I have set it to store messages locally but not to delete anything from the server as I want all my mail to be available via webmail if I am not using Thunderbird or my normal PC.

Looking at the activity manager, when I start Thunderbird this is what appears to be happening:

1.  A raft of folders gets deleted by Thunderbird (the message "Deleted folder Sent Items", "Deleted folder Read" etc. followed by the account name appears in the activity manager

2.  All folders are still there under each account in the left-hand pane, so they must be re-created immediately

3.  The message column settings I have previously set for these folders (sort order, order of columns etc.) is forgotten and the default settings are used.

4.  Downloading then begins, first of the headers, then of the messages, in these folders, followed by indexing.  There are 8 mailboxes which I have in Thunderbird so it takes a very long time and is pointless because it did exactly the same thing last time I started Thunderbird.

I don't understand why this happens: I just want Thunderbird to download any new messages each time instead of appearing to start from scratch every time I load it.  What am I doing wrong and how can I fix it?

---

### Post by guestolo on 2012-01-17
See if you can find any help in the following link
[http://kb.mozillazine.org/Duplicate_messages_received](http://kb.mozillazine.org/Duplicate_messages_received)

Edit>> Is mentioned in the first link, but don't overlook the possibility of a possible fix
[http://kb.mozillazine.org/Repeatably_downloading_the_same_messages](http://kb.mozillazine.org/Repeatably_downloading_the_same_messages)

---

### Post by SillySod on 2012-01-19
Thanks for the suggestions, unfortunately they didn't help: the first one is about multiple copies of the same message turning up in inboxes (not messages being wiped from local storage and re-downloaded again which is the problem I am having) and the second one relates to POP servers but my mail server is IMAP.

I think I've solved the problem though, which appears to arise from a bug in Thunderbird which nobody seems to want to acknowledge or resolve.  On start up, it tries to access subscribed folders from the server, but if it doesn't make an immediate connection, it decides that the user has unsubscribed from that particular folder and deletes it.  Then when the internet connection catches up and it can find the folder online and realises that it is subscribed, it re-creates it (reverting to default sort order and column settings) and re-downloads all the thousands of messages that it just deleted in order to synchronise.

The solution is to untick "Show only subscribed folders" in Server Settings...Advanced for each mailbox.

---

### Post by guestolo on 2012-01-22
You should mark this as Solved
Take note
I don't have my google account set up with an IMAP server, instead I vouched for the POP

I couldn't see the options you see with my setup
However, I do have an old Netscape account set up with IMAP servrer
I keep that option selected with no problems?

---

### Post by I_can_see_the_light on 2012-01-22
> **SillySod said:**
> The solution is to untick "Show only subscribed folders" in Server Settings...Advanced for each mailbox.

Hmm, I've that check box ticked and don't experience that problem, but I only have one gmail account though. 

In the *IMAP server directory* field I've entered ```
[Gmail]
```
Doing this makes the folder structure look nicer (unless they changed someting in the later versions of Thunderbird and made this setting obsolete) :

---

