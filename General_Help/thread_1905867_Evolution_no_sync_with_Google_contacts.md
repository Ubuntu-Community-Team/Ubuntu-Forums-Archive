---
title: "Evolution no sync with Google contacts"
date: 2012-01-07
forum: General Help
---

### Post by BertN45 on 2012-01-07
This is the last problem I have with the PIM stuff, I sync my Google mail, contacts and calendars with my Samsung GT-S5260 gsm and with Evolution, but Evolution has a problem with the contacts [78].

I did set up evolution to sync Email, Contacts and Calendars. Email and Calendar were OK, but Contact Sync did not work. After go-ogling I found an advice to go into "Passwords and Keys" and delete the entry with "Google" and I did so. After starting Evolution again, it asked for the password in the contacts screen and loaded the contacts. I changed a little bit the lay-out of contacts and felt happy.

I closed Evolution again and when I restarted Evolution all my contacts had disappeared. Whatever I try, I cannot get my contact to reappear nor is it possible to delete the Google address book. The contacts in Google itself are correct and have not changed.

It looks like an authorization issue and my entries in "Password and Keys" are:

imap://<myname>@imap.gmail.com/ [SIZE="1"]imap://<myname>@imap.gmail.com[/SIZE]
caldav://<myname>@%40gmail.com@www.google.com/calendar/dav/<myname>@gmail.com/events [SIZE="1"]caldav://<myname>@gmail.com@www.google.com[/SIZE]

I do not know, but probably I am missing an entry for the contacts. If you use gmail and contact sync, please look in "Passwords and Keys", please check whether I am missing an entry? 

Any other suggestion is also most welcome!

---

### Post by NMathisen on 2012-01-11
I am experiencing the same as above and only have two entries in "Passwords and Keys".  One for incoming server and one for outgoing server.

Calendar sync works great and as expected, just no contacts. Would really like to see a fix/workaround for this soon.

---

### Post by goranp on 2012-01-19
Yes same here. But for google apps eg. my company mail that is on another domain it  works fine. Contacts are available. Just it does not work for @gmail.com domain.

---

### Post by goranp on 2012-01-19
There is some annoying workaround 
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/883417](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/883417)

---

### Post by BertN45 on 2012-01-23
OK, that workaround worked for me too. Thank you

---

