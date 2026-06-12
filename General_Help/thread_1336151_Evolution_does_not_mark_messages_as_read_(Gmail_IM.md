---
title: "Evolution does not mark messages as read (Gmail IMAP)"
date: 2009-11-24
forum: General Help
---

### Post by Sprocketjoo on 2009-11-24
I know this is an old issue. Found some old threads in forum archives but I was not allowed to "bump" them.I thought this was supposed to be fixed a couple of releases ago. 

Problem is quite simple: I access my gmail account with evolution. Everything is fine but one thing. Whenever I read a message in Inbox, evolution will mark it as read as expected. However this won't be synchronized to Gmail, so checking gmail through webmail page will reveal the message still unread. Also, applications like cgMail will keep displaying the "old" number of unread messages (which proves the problem is in evolution not sending the sync info).

I guess a bunch of people is using this Gmail+IMAP+evolution scheme. Do you guys have this issue as well?

---

### Post by dcstar on 2009-11-25
> **Sprocketjoo said:**
> I know this is an old issue. Found some old threads in forum archives but I was not allowed to "bump" them.I thought this was supposed to be fixed a couple of releases ago. 

Problem is quite simple: I access my gmail account with evolution. Everything is fine but one thing. Whenever I read a message in Inbox, evolution will mark it as read as expected. However this won't be synchronized to Gmail, so checking gmail through webmail page will reveal the message still unread. Also, applications like cgMail will keep displaying the "old" number of unread messages (which proves the problem is in evolution not sending the sync info).

I guess a bunch of people is using this Gmail+IMAP+evolution scheme. Do you guys have this issue as well?

What are the options in the Account Preferences?

---

### Post by Sprocketjoo on 2009-11-25
Receiving Email:

imap.gmail.com:993
SSL encryption
Password Check For Supported Types
Remember Password

Receiving Options
No option checked here. 
Of course I don't want to "Automatically synchronize remote mail locally"

Sending:
SMTP
smtp.gmail.com:587
Server Requires authentication
TLS encryption
PLAIN Check for Supported Types
Remember Password

Rest of options are set to default or unchecked

---

### Post by Sprocketjoo on 2009-11-25
Duplicate. Sorry

---

### Post by lightstream on 2009-11-27
Just thought I'd add that evolution with IMAP works fine for me, as far as marking messages as read goes. 

I don't use GMail though, this is a private email server.

---

