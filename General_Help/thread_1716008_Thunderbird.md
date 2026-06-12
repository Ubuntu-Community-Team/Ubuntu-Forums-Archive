---
title: "Thunderbird"
date: 2011-03-27
forum: General Help
---

### Post by nkae100 on 2011-03-27
Does anyone know why Thunderbird downloads the entire content of my Inbox and Sent folder every time I load it? Its really annoying.

---

### Post by Shmantiv_Radio on 2011-03-27
Ummm, it's supposed to do that. 

Haven't you used an email client before?

---

### Post by SeijiSensei on 2011-03-27
Are you using POP3 or IMAP?  If POP3, do you have Thunderbird configured to leave your mail on the server?  POP servers are supposed to keep track of which messages you've read in these cases, but they don't always do a good of that.  If you have IMAP as an option, I'd suggest switching to that.  All your mail will remain on the server, and Thunderbird will remain synchronized with your inbox without any effort on your part.

---

### Post by nkae100 on 2011-03-27
I use IMAP.

In "Account Settings" > "Synchronization & Storage" I have an option called "Keep messages for this account on this computer". I have an option unticked because I am not sure if toggling it will mean downloading the content of my account and removing it from the server.

---

### Post by SeijiSensei on 2011-03-28
> **nkae100 said:**
> I use IMAP.

In "Account Settings" > "Synchronization & Storage" I have an option called "Keep messages for this account on this computer". I have an option unticked because I am not sure if toggling it will mean downloading the content of my account and removing it from the server.

No, I have that option checked, and all my messages remain on the server.  What that option does is create local copies of the remote folders.  That's a convenience if you travel and don't want to have to connect to the server to consult your past messages.  You'll see these folders in ~/.thunderbird/[something].default]/ImapMail/server_name.  

I'm guessing if you check that box, you won't see your entire mailbox being downloaded repeatedly.  However if you're tight on disk space you might want to think about culling some junk from your folders before enabling it.

---

### Post by Nutria on 2011-03-28
> **nkae100 said:**
> Does anyone know why Thunderbird downloads the entire content of my Inbox and Sent folder every time I load it? Its really annoying.

You'll just have to get used to it.  The problem is that Tbird treats IMAP like a fancy POP.

---

