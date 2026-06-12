---
title: "How To Migrate Email (One Web Host to Another)"
date: 2010-01-23
forum: General Help
---

### Post by noloader on 2010-01-23
Hi All,

Sorry about the cross post with Desktop. I was not sure if Desktop meant 'Desktop vs Server', or Desktop as in relation to Windows Managers.

I'm hoping someone else has worked out these details and can offer some help. I want to move a domain from one web host to another. I also want to preserve my email. Does anyone have a recommendation for software which will allow me to:

(1) Copy current web host email locally
(2) Switch web hosts
(3) Populate new web host with local copy

I've looked at imapcopy and imapsync. Unfortunately, both want Server -> Server. I briefly looked at setting up a local IMAP server (dovecot-imap), but it is clear that this is more ISP-grade. I did not see a quick example of user management in [http://wiki.dovecot.org/HowTo](http://wiki.dovecot.org/HowTo), and I don't really want to spend days working on the configuration.

Any recommendations for software that allows me to 'backup' and 'restore' to/from a local file store?

Thanks,
JW

---

### Post by blueridgedog on 2010-01-23
Ask your new webhost provider what methods of import, if any, they support.  They may give you more options than you are considering.  

Alternatively, setup a gmail account and suck in all the existing email and live with it there.

---

### Post by terrapin893 on 2010-01-23
Connect to your current mail server using IMAP, then download all of your messages to your local machine through whatever mail client you are using.  Then just configure your new email account with the same client.

---

### Post by noloader on 2010-01-27
Hi Terrapin893,

> **terrapin893 said:**
> Connect to your current mail server using IMAP, then download all of your messages to your local machine through whatever mail client you are using.  Then just configure your new email account with the same client.
This is what I initially drempt up. Have you tried this? I'm concerned that after switching web hosts, Thunderbird will delete all local messages since the email accounts will be empty on the new web host.

Jeff

---

### Post by noloader on 2010-01-27
Hi [blueridgedog]("http://ubuntuforums.org/member.php?u=459469"),
> **blueridgedog said:**
> Ask your new webhost provider what methods of import, if any, they support.  They may give you more options than you are considering.
I don't think either web host will help: the old web host is losing business, so he will probably be less than interested. The new web host wants the monthly fees (and perhaps a setup fee). They don't want to really do anything out of the ordinary...

JW

---

### Post by t4thfavor on 2010-01-27
I have always had luck setting both accounts up as an IMAP account, then selecting all and moving them into the new hosts folder (like a folder called fromOldHost).
If they allow IMAP, then you can do it that way. Be patient as it will probably take a long time.

---

