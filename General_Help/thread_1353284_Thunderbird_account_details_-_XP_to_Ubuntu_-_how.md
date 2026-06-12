---
title: "Thunderbird account details - XP to Ubuntu - how?"
date: 2009-12-12
forum: General Help
---

### Post by zozza on 2009-12-12
I had a large number of POP3 accounts on Thunderbird in XP.  Therefore I copied over the /Mail directory to Ubuntu and all my folders and e-mails appeared.  

However, the accounts do not appear in the Accounts options (Edit / Account Settings).  I can set these up manually but was wondering if there is a way to do this automatically?

Is there a particular file I copy over for example - cannot see anything obvious.

Thanks.

---

### Post by kellemes on 2009-12-12
You need to copy whole profile-folder from the Windows-install ([Locate your profile folder]("http://www.mozilla.org/support/thunderbird/profile#locate")) to whatever place you want it to be..
Note: you want everything under the folder made of 8 random characters, that's the profile-folder.

Now, from Ubuntu you can do the following from a terminal-window..
```
thunderbird -profilemanager
```
Here you can create a new profile and simply point this new profile to the profile-folder you just copied..

I've done this millions of times and it works fine.. all info (including account information) is 'imported'.

---

