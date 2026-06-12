---
title: "Combine IMAP acounts"
date: 2011-04-01
forum: General Help
---

### Post by megabuffen on 2011-04-01
I currently have 7 different email accounts that I use with evolution and I don't enjoy having 7 different inboxes. I can't use POP because I need to access my mail from different computers with different operating systems.

Is there any way to make all the messages from my different IMAP accounts show up in one single inbox?

---

### Post by megabuffen on 2011-04-01
Okay, no ideas?

Then is there some way that I can create 'favorites', like in outlook where all the inboxes can be displayed as quick links so I don't have to expand the tree for each account to show the inbox.

---

### Post by texpat on 2011-04-01
I suppose that you could create a filter (Edit/Message Filters) to copy incoming e-mails to whatever folder you want.

---

### Post by megabuffen on 2011-04-01
What kind of filter would I use to move incoming mail from he inbox of one account to the inbox of another one? What are the rules for it? Also, is it possible to store sent messages in the sent messages folder of a GMail account that Ia ccess through IMAP?

I tried adding a rule that would check if the recipient is NOT a specific address so basically it would validate as true for almost all email. I then set the action to move it to the inbox of another account, but it doesn't seem to work.

---

### Post by texpat on 2011-04-01
OK, so here's what I tried:

I created a rule where the condition is that the sender contains '@', which should apply to all of them.

If that rule is met, I have the e-mail copied to a folder (the dialogue lets you create a new one, which may come in handy) in my main account (i.e. the one called On This Computer).

I haven't tested this too extensively, but is seems to work.

---

