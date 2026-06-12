---
title: "Thunderbird can't delete emails"
date: 2010-05-17
forum: General Help
---

### Post by Mike.lifeguard on 2010-05-17
I have two emails in my Inbox marked as new. I cannot delete them, move them, or mark them as read.

Attempting to delete them fails with the message

```

Unable to delete messages in folder Inbox because it is in use by some other operation. Please wait for that operation to finish and then try again.

```

Other operations fail silently. No other operations are listed in the activity manager (which doesn't actually let you /manage/ activities... just view them).

How can I force deletion of these emails? Where in the filesystem are they stored?

---

### Post by BoneKracker on 2010-05-17
Somebody correct me if I'm wrong, but I think Thunderbird uses mbox, so there isn't a file for each message, just a file for each mailbox.  In other words, there aren't two little files sitting somewhere you can simply delete.

There may be a lock on the mailbox file.  Make sure you don't have two instances of Thunderbird open, or that you don't have those messages open in another window or something.  Try rebooting to release the lock.

If that doesn't work, I seem to recall Thunderbird has some function that "compacts" a folder or mailbox.  That might resolve it. 

If you're desperate, you could trash the whole mailbox file (it's buried somewhere in a Mozilla/Thunderbird-related folder in your home directory). Theoretically, I think you could edit the mailbox file and delete the messages (it should be a text file).  You might also be able to research what locking mechanisms Thuderbird uses (it probably creates a tiny "lock file" somewhere you could delete).

I'm guessing your using POP, but if you're using IMAP this could be something else beyond my understand (like you need to set an option for "on delete remove from server immediately" or something).

---

### Post by Vladimir Hidalgo on 2010-05-17
This happen very often, to me this happen most frequently when I delete mail before the sync process is finished. Mail entries get stuck and you can't interact anymore with them.

Only solution I'd found in those cases is to restart Thunderbird.

---

### Post by Mike.lifeguard on 2010-05-17
> **Vladimir Hidalgo said:**
> This happen very often, to me this happen most frequently when I delete mail before the sync process is finished. Mail entries get stuck and you can't interact anymore with them.

Only solution I'd found in those cases is to restart Thunderbird.

I had to close TB and leave it closed for a while. I guess indexing continues in the background even if the main window is closed. This along with email move/delete not being atomic really need to be resolved by the TB team. It's been going on for years.

---

### Post by Vladimir Hidalgo on 2010-05-17
I guess until it's resolved it's better to not touch anything while a sync operation is ongoing.

Atomic operations in TB are years behind other mail software, but TB is superior in everything else... what an irony.

---

