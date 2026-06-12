---
title: "Evolution Mail"
date: 2010-08-13
forum: General Help
---

### Post by Flanker37 on 2010-08-13
Hi guys, im using Evolution mail for the first time.  I thought it would be similar to using Outlook Express.

I went through the motions on the setup wizard. Presto, mail in my mailbox.

But i was horrified to find out that when i logged into the web based side of hotmail, my inbox is empty :shock:

Has Evolution completely wiped my mail from hotmails servers?
Is my email now permanently downloaded to my PC?
What happens if i want to erase my HD and install a different OS?

---

### Post by oleink on 2010-08-13
> **Flanker37 said:**
> Hi guys, im using Evolution mail for the first time.  I thought it would be similar to using Outlook Express.

I went through the motions on the setup wizard. Presto, mail in my mailbox.

But i was horrified to find out that when i logged into the web based side of hotmail, my inbox is empty :shock:

Has Evolution completely wiped my mail from hotmails servers?
Is my email now permanently downloaded to my PC?
What happens if i want to erase my HD and install a different OS?

yes it deleted it from the server.  There may be a way to re upload it.  You can only save POP server emails to the server even after downloading them.  Yes they're on your computer

---

### Post by jcolyn on 2010-08-13
If you want evolution to leave mail on the server you need to go to edit-preferences- then highlight the account and click edit. Click receiving options and check the box leave messages on server. Close and restart evolution..

---

### Post by Flanker37 on 2010-08-14
what a stupid program.  Those should not be the default settings.  How many people using ubuntu for the first time are going to fall into the same trap.

Outlook doesn't remove emails from hotmails servers

---

### Post by HermanAB on 2010-08-14
It depends on the protocol you configure.  If you configure POP, then that is how it will behave.

The way to get the mail back on the server is with IMAP. First set the POP account to 'keep' the mail on the server - else it will download it all again. Now configure a second account, this time using IMAP.  Then simply click-drag-drop all the mail (ctrl click to highlight all) from the POP account to the IMAP account and it will all go back to the server - unaltered.  Finally, remove the POP account.

---

### Post by oleink on 2010-08-15
> **Flanker37 said:**
> what a stupid program.  Those should not be the default settings.  How many people using ubuntu for the first time are going to fall into the same trap.

Outlook doesn't remove emails from hotmails servers

That is just the way MOST e-mail servers work unless you configure POP

---

