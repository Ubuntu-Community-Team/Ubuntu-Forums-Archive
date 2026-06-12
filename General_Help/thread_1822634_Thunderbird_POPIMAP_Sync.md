---
title: "Thunderbird POP/IMAP Sync"
date: 2011-08-10
forum: General Help
---

### Post by Gordon D on 2011-08-10
Hi,

Not sure if I have posted this to the correct forum.

I run a number of PCs and laptops. I use Thunderbird as my email client. On my main PC, Thunderbird is configured for POP/SMTP to enable all my incoming and outgoing emails to be stored locally. These go back several years, so storing them on the IMAP server isn't an option.

I have other PCs that I use, and these are configured to use IMAP, and outgoing emails go to the Sent folder on the IMAP server.

I am looking for a way to copy the messages in the IMAP sent folder to the POP configured local Sent folder on my main PC.

The obvious way would be to configure the IMAP account on the main PC and just drag and drop them in, but I am hoping there is a simpler and more automated way of doing this.

Any ideas would be much appreciated.

Cheers

Gordon

---

### Post by Habitual on 2011-08-15
Gordon:

Create another IMAP account on the same host as POP/SMTP **then drag** from IMAP/sent to Local/sent?
Then delete IMAP account.

Should work.

---

### Post by Gordon D on 2011-08-18
This is the solution I came up to with this.

On the Thunderbird configuration on the IMAP machines under Copies & Folders, I check the "Place Replies in the folder of the message being replied to" box. This puts a copy of the outgoing message in the Inbox of the IMAP folder.

I then setup a filter on the POP machine to move any emails received from myself into the local Sent folder.

Not sure if this is of any interest, as the response wasn't overwhelming :)

---

### Post by Gordon D on 2011-08-18
> **Habitual said:**
> Gordon:

Create another IMAP account on the same host as POP/SMTP **then drag** from IMAP/sent to Local/sent?
Then delete IMAP account.

Should work.

Thanks for the response. I tried this, but it was very confusing to manage on an ongoing basis. I have posted another solution that I am now using.

Many thanks again.

---

