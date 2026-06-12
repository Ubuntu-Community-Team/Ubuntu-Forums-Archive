---
title: "Evolution E-Mail: Restore a Single Folder?"
date: 2011-01-25
forum: General Help
---

### Post by demonGeek on 2011-01-25
I accidentally deleted a single (IMAP) folder from Evolution and expunged it.  I have a backup tar file (created using Evolution's Backup Settings option) which has the missing folder and its contents but I can't figure out how to restore just the one folder.

The backup is simply a tar of my .evolution directory so all the folders and files are available but I need a way to import them into Evolution so that the database gets updated.  The Import option doesn't offer anything useful.

Any ideas?

Thanks.

---

### Post by demonGeek on 2011-01-27
** bump **

---

### Post by Habitual on 2011-01-28
If you deleted an IMAP folder using an IMAP'd client, the folder is gone from the server and consequently from the client.

---

### Post by demonGeek on 2011-01-28
I don't think you read my original post properly.

---

### Post by lisati on 2011-01-28
> **demonGeek said:**
> I don't think you read my original post properly.

I don't think you read the reply properly. :)

If you delete an IMAP folder, it's effectively gone from the server, which is where IMAP folders are stored.

On the occasions I've restored Evolution settings from a backup, I've never noticed an option to restore individual folders.

---

### Post by demonGeek on 2011-01-28
Yeah, that's what I was afraid of - I don't want to restore everything, only the missing bits.  

In Outlook, I'd just drag the message files into Outlook and drop them there and it would add them to the mail database.  Seems like Evolution can't do that.

It's a shame really - the code that does the full restore must actually be restoring one folder at a time so the functionality is there, just not exposed.

Thanks anyway.

---

### Post by Habitual on 2011-01-29
lisati:

Thanks for the confirmation. I always hesitate on the inevitable answers ("Your OS/app/whatnot **is** toast") because one person doesn't have all the answers.

But then again, some things* never *change, thank God.

---

### Post by tredegar on 2011-01-29
I don't think all is lost when you have a backup of the directory.

Can't you just stop evolution, put the folder back where it belongs, start evoution ?

Evolution seems to keep my mail in **~/.evolution/mail/local/Inbox**

There is also **~/.evolution/mail/local/Inbox.cmeta** and a bunch of other extensions.
If I stop evolution, rename those indexes or whatever they are to their **name.bak** when I restart evolution the original files are regenerated from the data in **~/.evolution/mail/local/Inbox** and everything is file.

So I suggest you, stop evolution, then just restore the missing file, but not the indexes or .cmeta files.
Then start evolution, and it'll probably sort itself out.

Let us know how you get on.

---

### Post by fonsi2099 on 2011-07-12
After put the folder back where it belongs, I start evolution  but I can not open the files because Evolution close immediately, any solution?
Thank you 
:)

---

### Post by FLOZz on 2011-09-03
If you have a backup of the Evolution cache folder (~/.local/share/evolution/mail/imap/*) you can try this script:  

[http://bzr.flogisoft.com/evolution-imap-cache-to-mbox/](http://bzr.flogisoft.com/evolution-imap-cache-to-mbox/)  

And then you will be able to re-import your mail from the .mbox file.

---

