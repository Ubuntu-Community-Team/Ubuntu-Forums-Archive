---
title: "postfix/evolution issue"
date: 2010-04-24
forum: General Help
---

### Post by ryanf4321 on 2010-04-24
I wasn't sure where else to post this, but I'm trying to get postfix maildir style mailboxes working using imap and evolution. I can send back and forth fine to other users on the system, but I want to be able to send and receive mail with an external address as well, say my gmail account. I can send mail using evolution to my gmail from my system, but for whatever reason I can't seem to receive mail from it. I'm not sure what to do. Nothing appears in the Maildir folder. I don't know where the problem is, with postfix or evolution. Any suggestions?

---

### Post by Kljuka on 2010-04-24
If I understand correctly, you can send mail with gmail (from gmail.com), but can't recieve it?
First check if your DNS MX records are correct. They should have your server's address.

---

### Post by ryanf4321 on 2010-04-24
well its that i can send mail to [email]myname@gmail.com[/email] from myname@localhost just fine, but when i try to reply to it, i don't see anything in my maildir box, but the mail still "sends". I guess I don't understand how to let gmail know where to reply back to. In main.cf in postfix theres so many confusing fields: mydestination, myhostname, mynetworks, etc. I don't know what to edit and what to leave alone.

---

### Post by dcstar on 2010-04-25
> **ryanf4321 said:**
> well its that i can send mail to [email]myname@gmail.com[/email] from myname@localhost just fine, but when i try to reply to it, i don't see anything in my maildir box, but the mail still "sends". I guess I don't understand how to let gmail know where to reply back to. In main.cf in postfix theres so many confusing fields: mydestination, myhostname, mynetworks, etc. I don't know what to edit and what to leave alone.

**myname@localhost** is for internal use only. That is not a email address that is accessible externally.

Use you proper e-mail address for **all **external communication.

Unless you have a proper DNS entry and a system set up to receive mail for it you cannot send mail to your system externally.

---

### Post by ryanf4321 on 2010-04-25
ok, that makes sense why it won't work then, but how do I set up a DNS entry? What other files do I need to possibly edit other than main.cf in postfix? I wish I could find a clear walkthrough of this but I really haven't found one.

---

### Post by ryanf4321 on 2010-04-25
and also, how do i find out what my external email refers to my system as ( myusername@something ) so that I can receive the mail?

---

### Post by dcstar on 2010-04-26
> **ryanf4321 said:**
> and also, how do i find out what my external email refers to my system as ( myusername@something ) so that I can receive the mail?

You **cannot** receive mail unless you pay for a Domain Name and set up a mail server on a static IP address.

If you want a mail server then look at the many HOWTOs already around.

---

