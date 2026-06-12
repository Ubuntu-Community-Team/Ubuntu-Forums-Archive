---
title: "Evolution Server Synchronization"
date: 2010-10-01
forum: General Help
---

### Post by Eric.B on 2010-10-01
Hi,

I have about a dozen email accounts on one server and I'm able to get Evolution to connect/download via IMAP.  However my problem is with Evolution only creating a local copy of what is on the server.  I would like items deleted from Evolution to also be removed off my mail server.  Is there a setting somewhere I'm missing for this?

I've searched the net and the forum for this answer with not much luck....

Thanks in advance,
Eric

---

### Post by dcstar on 2010-10-02
> **Eric.B said:**
> Hi,

I have about a dozen email accounts on one server and I'm able to get Evolution to connect/download via IMAP.  However my problem is with Evolution only creating a local copy of what is on the server.  I would like items deleted from Evolution to also be removed off my mail server.  Is there a setting somewhere I'm missing for this?

I've searched the net and the forum for this answer with not much luck....

Thanks in advance,
Eric

When you delete IMAP messages Evolution tags them as deleted and moves them to its local Trash folder for that account. Simply emptying that Garbage Bin will permanently delete them from the IMAP server.

---

### Post by Eric.B on 2010-10-02
David,

Thanks for that bit of insight.  I will have to play with it more.  When I close evolution (without expunging each trash folder) and reopen evolution, the trash seems to be empty, yet if I log into my server I can see the old messages are still sitting in the inbox marked as read.  Perhaps each trash folder must be emptied before I close Evolution?  Not very convenient but I'll see if I can figure out how to make it work.

Thanks.

---

