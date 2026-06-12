---
title: "Copy / Import Evolution mail"
date: 2011-06-07
forum: General Help
---

### Post by pocon on 2011-06-07
I have an old hard drive that has my evolution contact list and emails on it, I was wondering if it was possible to copy them over to a new drive.

The new drive has a clean install of Ubuntu 11.04. I was able to copy over documents in my home directory successfully - but am not sure what to do to get the evolution data over. I do have the same POP3 account set up and working again, just no emails or contact list.

The old drive is no longer boot-able for some reason - but I can connect to it by loading it into a hard drive caddy and copy files over that way, I just don't know what to copy...

---

### Post by Habitual on 2011-06-07
should be a hidden dot directory. Browse using nautilus and press Ctrl+H to see hidden content.

It "may" be under ~/.local/share/evolution
if it is, just copy it to new hard drive, same location

I see the following:
addressbook
calendar
categories.xml
mail
memos
tasks

but I don't have Evolution installed.

HTH.

---

### Post by pocon on 2011-06-07
Thanks for the quick response! 
I'll give it a try and report back.

---

### Post by pocon on 2011-06-07
Well, that's where it is on my new hard drive - but not the old.

Got some more info to release - probably should have said it before - the old drive had Ubuntu 10.10...

---

### Post by ttguy on 2011-06-08
On my 10.10 you have a
/home/<userid>/.evolution

folder and this contains all your settings and data for evolution. 

You should be able to just copy that folder to your new drive

---

### Post by pocon on 2011-06-08
there's such a folder, and I copied it over - but no joy.
I looked at it's contents, it has a mail folder, and in it there's one file named folders.db. In the new drive at the ~/.local/share/evolution location there's mail/local and a bunch of files and folders: ie Inbox, Drafts, Sent...

---

