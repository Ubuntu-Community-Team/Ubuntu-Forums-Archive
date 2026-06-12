---
title: "Two computers with same email adress in Evolution problem"
date: 2010-06-23
forum: General Help
---

### Post by mrpenguin on 2010-06-23
I have a Gmail account and a laptop and a netbook, I use both my computers.
At the moment when i download mail from the server in Evolution on one of my computers it wont download the same email to the other computer as well.
My setting is set that my mail stay on the server .... is there any way i can get my mail in both computers when fetching new mail ?

---

### Post by dcstar on 2010-06-24
> **mrpenguin said:**
> I have a Gmail account and a laptop and a netbook, I use both my computers.
At the moment when i download mail from the server in Evolution on one of my computers it wont download the same email to the other computer as well.
My setting is set that my mail stay on the server .... is there any way i can get my mail in both computers when fetching new mail ?

If you mean that you cannot download mail using POP at the exact same time from the same account, then of course not as only one POP connection is allowed at a time as the protocol locks the mailbox.

If you need synchronised e-mail then use IMAP - do a search to see if it is supported by your e-mail provider.

---

### Post by tad1073 on 2010-06-24
IMAP is supported with gmail

---

### Post by John Bean on 2010-06-24
> **tad1073 said:**
> IMAP is supported with gmail

...and it works :-)

[http://mail.google.com/support/bin/answer.py?answer=78799&topic=12814](http://mail.google.com/support/bin/answer.py?answer=78799&topic=12814)

---

### Post by mrpenguin on 2010-06-24
What I mean is that I have two computers ... when I go into Evolution on the one computer and download my mail from gmail into my evolution inbox and then later in the day go on my other computer and go in to evolution and download my mail into my evolution inbox i want to get the same mail that i downloaded onto the other computer before.

In other words have the same mail in two inboxes on two different computers ... dont care about send mail

---

### Post by tad1073 on 2010-06-24
> **mrpenguin said:**
> What I mean is that I have two computers ... when I go into Evolution on the one computer and download my mail from gmail into my evolution inbox and then later in the day go on my other computer and go in to evolution and download my mail into my evolution inbox i want to get the same mail that i downloaded onto the other computer before.

In other words have the same mail in two inboxes on two different computers ... dont care about send mail

[http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol](http://en.wikipedia.org/wiki/Internet_Message_Access_Protocol)

IMAP is what you want to use

SMTP is the sending protocol

[http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol](http://en.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)

---

### Post by dandnsmith on 2010-06-24
Just in case it might help (a paucity of detail given), Googlemail is not the only email provider which doesn't care about any 'leave on server' setting in your email client - it does what the settings at the googlemail (or other) mailbox says. The default setting is, often, to only supply emails not already read/downloaded.

---

### Post by dino99 on 2010-06-24
> **dandnsmith said:**
> Just in case it might help (a paucity of detail given), Googlemail is not the only email provider which doesn't care about any 'leave on server' setting in your email client - it does what the settings at the googlemail (or other) mailbox says. The default setting is, often, to only supply emails not already read/downloaded.

yeah if the mail is downloaded on the first pc and is set to NOT leave on the sever, then what can he expect :lolflag:

---

### Post by Javich on 2010-06-24
Hey mrpenguin,

A reliable way that I use to get the same results on multiple accounts is to configure certain options in the e-mail client, that way I can keep synchronized my email clients on linux and my job's box (vista); this is archieved by allowing the client to leave the mail in the pop server

Open Evolution
go to "Edit" -> "Preferences" then click on the account you want to keep in sync on 2 computers.
Click the "Edit" button, go to the "Receiving Options" tab and make sure the checkboxes are selected:
  - Leave messages on server
  - Delete after "x" days (I usually use 15)

Then go do the same on your other box.

btw, if an e-mail has been already downloaded on machine "a", then on machine "b", the e-mail will still be in the pop server, but if you sync again either on "a" or "b" it will not be downloaded anymore and will be deleted when it gets "x" days old.

---

### Post by dandnsmith on 2010-06-25
My point was, that if the mail server acts like google, then you can set whatever options you like in evolution (or whatever), and not affect what google does about keeping the messages.

---

### Post by philinux on 2010-06-25
Dont know why gmail is not behaving as it should.

I have 2 pc's in different locations and a lappy. My Hotmail and my isp mail all appear on all pc's using pop.

I have it set to leave on server.

---

