---
title: "Evolution Can not delete emails"
date: 2011-02-06
forum: General Help
---

### Post by bigwoof on 2011-02-06
Hi THere 

I am having trouble with evolution.  There are 6 unread emails in my inbox but they have no body, when I open them I get the following: 

Unable to retrieve message
Could not find message body in FETCH response.

When I access the emails through my browser they are not on the server.  

I am using IMAP to sync my mail.  I am running ubuntu 10.04 and Evolution 2.28.3

Is there a way to purge the list of headers and then get them back form the server?  

Cheers

Phil

---

### Post by dcstar on 2011-02-07
> **bigwoof said:**
> Hi THere 

I am having trouble with evolution.  There are 6 unread emails in my inbox but they have no body, when I open them I get the following: 

Unable to retrieve message
Could not find message body in FETCH response.

When I access the emails through my browser they are not on the server.  

I am using IMAP to sync my mail.  I am running ubuntu 10.04 and Evolution 2.28.3

Is there a way to purge the list of headers and then get them back form the server?  

Cheers

Phil

Make sure you have the "Automatically Synchronise remote mail locally" Receive option set for that IMAP account.

---

### Post by bigwoof on 2011-02-07
> **dcstar said:**
> Make sure you have the "Automatically Synchronise remote mail locally" Receive option set for that IMAP account.

Thanks for the suggestion, I already had "Automatically Synchronise remote mail locally" set for that account, so I tried to turn it off and on again, but I had no luck.

I also upgraded to the Evolution 2.30 in the hope that it would help things but no luck.

Any other suggestions?

Cheers

Phil

---

### Post by bigwoof on 2011-02-08
I think I have solved the problem.

It seemed to be a problem with the database.  Please note that I came up with this solution by sheer luck.  For anybody else doing this please do so with care - I have no idea if it is a good way to fix the problem or not.

What I did was:

1. Close down evolution

2. Rename the email database located at:

```
~/.evolution/mail/imap/[email_account]/folders.db
```

to 

```
~/.evolution/mail/imap/[email_account]/folders.db.old
```

3. Open Evolution and it will rebuild the database from the server without the annoying persistent emails.

Cheers

Phil

---

