---
title: "Evolution 3 &amp; Google Calendar sync."
date: 2011-10-20
forum: General Help
---

### Post by izazou82 on 2011-10-20
Hello!! I recently installed Ubuntu 11.10 with GNOME 3, which is awesome! It comes with Thunderbird, but I chose to install Evolution 3 instead. The only problem I have is that I cannot sync evolution 3 with Google calendar. Can anyone help me please?? Thanks!!
--Isabelle

---

### Post by izazou82 on 2011-10-21
I continued looking on the web to find how to sync my Google Calendar in Evolution 3 (under Ubuntu 11.10/GNOME 3 shell) and saw a post from a Fedora user with the same issue.  I tried his solution and it worked!!! 
here it is: 

"I was digging in gconf-editor, because of another problem, and I found the evolution entry in apps/evolution
there is a key called "source" in addressbook and calendar also, and they differ. the calendar had no "google" source. I simply copied it from the addressbook part (double click on sources under addressbook, select the one with name="Google", press edit, copy it's content) and added a new entry to the source key under calendar (same procedure, but press add when editing the key).
At this point when switching to calendars in evolution, I had it there. I renamed it, and pressed ok, it asked for my password, AND THAT'S IT!

I think I had luck :D" --- Aron

from [http://www.lefred.be/?q=node/141](http://www.lefred.be/?q=node/141)

THANKS!!!!! :)

---

