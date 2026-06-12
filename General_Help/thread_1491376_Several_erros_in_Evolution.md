---
title: "Several erros in Evolution"
date: 2010-05-23
forum: General Help
---

### Post by Livret on 2010-05-23
Hi,

I got the folowing error messages in my evolution status bar:

[LIST]
[*]Error while fetching email (which is weird, cause I can send and receive emails)
[*]Error while storing folder Inbox
[*]Error while generating message list (column folder_name is not unique)
[/LIST]

The messages started appearing afeter I had to force a shutdown.

Any help?

Thanks!

---

### Post by Livret on 2010-05-23
I did some research and for the "Error while generating message list" I tried the solution found here: [http://ubuntuforums.org/showthread.php?t=1279696](http://ubuntuforums.org/showthread.php?t=1279696)

using the command:

cd ~/.evolution/mail ; for i in `find . -name folders.db`; do echo "Rebuilding Table $i"; sqlite3 $i "pragma integrity_check;"; done


I got this: 


*** in database main ***
Page 242 is never used
rowid 59 missing from index sqlite_autoindex_folders_1
rowid 60 missing from index sqlite_autoindex_folders_1
rowid 61 missing from index sqlite_autoindex_folders_1
rowid 127 missing from index READINDEX-Inbox
rowid 127 missing from index JUNKINDEX-Inbox
rowid 127 missing from index DELINDEX-Inbox
rowid 127 missing from index sqlite_autoindex_Inbox_1
rowid 128 missing from index READINDEX-Inbox
rowid 128 missing from index JUNKINDEX-Inbox
rowid 128 missing from index DELINDEX-Inbox
rowid 128 missing from index sqlite_autoindex_Inbox_1
rowid 129 missing from index DELINDEX-Inbox
rowid 129 missing from index sqlite_autoindex_Inbox_1
rowid 130 missing from index READINDEX-Inbox
rowid 130 missing from index JUNKINDEX-Inbox
rowid 130 missing from index DELINDEX-Inbox
rowid 130 missing from index sqlite_autoindex_Inbox_1
rowid 135 missing from index READINDEX-Inbox
rowid 135 missing from index JUNKINDEX-Inbox
rowid 135 missing from index DELINDEX-Inbox
rowid 135 missing from index sqlite_autoindex_Inbox_1
wrong # of entries in index READINDEX-Inbox
wrong # of entries in index JUNKINDEX-Inbox
wrong # of entries in index DELINDEX-Inbox
wrong # of entries in index sqlite_autoindex_Inbox_1

---

### Post by t.rei on 2010-05-23
My evolution (upgraded today to v. 2.30.1.2) from the LTS repository is acting up.

No filters can be applied...
Error refreshing INBOX...
Weird missized icons...
Not closing properly (killed it after an hour or so of not-going away)

I absolutely hope this is getting fixed soonishTM. Currently I need this piece of software to work, thats why I was looking forward to a LTS candidate!

For something this fundamental - evolution being the central mail/calendar system - having this happen outside of an unstable branch is... horrible :(

---

### Post by Livret on 2010-05-26
After some research I think I found out why Evolution started to went nuts...

I imported my mail from outlook and the Inbox from there probably screwed up something - I moved all my mail to the Evolution Inbox and then deleted the Outlook Inbox, but still...

Other bizarre thing, my messages in the Evolution Inbox (and in the Inbox only) that were imported are now are duplicate, triplicated, qadruplicated....

---

