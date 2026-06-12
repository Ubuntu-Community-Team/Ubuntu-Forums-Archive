---
title: "Evolution - Gmail IMAP - Send messages duplicated"
date: 2009-09-08
forum: General Help
---

### Post by nomnex on 2009-09-08
Hi,

Anyone has an answer or idea? Have you experienced it?

Evolution + Gamil IMAP accounts. Everything goes fine, but the Send message folder. All the mails I send are duplicated.

Evolution Preferences > Defaults > Send and Draft messages:
Drafts folder: myusername/[Gmail]/Drafts
Send Messages folder:myusername/[Gmail]/Send message

I cannot believe it is a bug, but I don't see a single setting to change that. Thanks

---

### Post by nomnex on 2009-09-08
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/426583](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/426583)

---

### Post by samcompton on 2009-09-10
I fixed this by editing preferences in Evolution.  Go to Preferences, click on your gmail account and click edit.  Then click on the defaults tab.  Leave your drafts folder as the gmail drafts folder if that is where you would like your drafts to be kept.  Change your sent folder back to the default (on your machine) like in my attached screenshot.  Gmail will automatically put a copy in your Gmail sent folder and another in your local sent folder.  That is why we were getting duplicates.

---

### Post by nomnex on 2009-09-10
Hi, that exactly my conclusion and my current setting. That's also the reason I have filled a BUG - see link above. Fell to make voice by following it.

It is counter-intuitive to offer a folder redirection option if it creates duplicate messages. There should be an Evolution IMAP tutorial to save new comer some time during the setup.

I hope this thread can help others and BTW the print screen look nice :) See you.

---

