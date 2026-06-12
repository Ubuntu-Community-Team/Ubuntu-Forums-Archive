---
title: "SSH auto-login script using RSA"
date: 2010-09-14
forum: General Help
---

### Post by SuaSwe on 2010-09-14
Hi all,

I have a question about auto-login scripts for SSH where RSA keypair authentication is used.

Basically, I have a server (say, server1) configured with RSA keypair authentication. This server is connected to another server (server2), that I connect to via server1 and for which I use the same passphrase and public key as I use for server1. I was wondering if it is possible *without writing out the passphrase in a file* to "forward" the phrase on from server1 to server2 in an auto-login script, saving me having to type it in twice? Any ideas on how this might be done, if so?

Cheers all!

SuaSwe

---

### Post by SuaSwe on 2010-09-15
Anyone? :)

---

### Post by Baked- on 2010-09-15
This should help you

[http://www.semi-legitimate.com/sls/blog/36-tech-tips/65-automate-sftp-ssh-and-scp](http://www.semi-legitimate.com/sls/blog/36-tech-tips/65-automate-sftp-ssh-and-scp)

---

### Post by SuaSwe on 2010-09-15
I think that just describes how to set up RSA keypair authentication, which I already have. :) I'm looking to find out how to transport the passphrase from one login instance to another without having to type it in twice or save it in clear text anywhere, if possible.

> **SuaSwe said:**
> Hi all,
... I have a server (say, server1) configured with RSA keypair authentication. This server is connected to another server (server2), that I connect to via server1 and for which I use the same passphrase and public key as I use for server1. I was wondering if it is possible *without writing out the passphrase in a file* to "forward" the phrase on from server1 to server2 in an auto-login script, saving me having to type it in twice? 
SuaSwe

---

### Post by Baked- on 2010-09-15
> **SuaSwe said:**
> I think that just describes how to set up RSA keypair authentication, which I already have. :) I'm looking to find out how to transport the passphrase from one login instance to another without having to type it in twice or save it in clear text anywhere, if possible.

If you use key authentication a passphrase shouldn't be needed.  For example, when i login to one of my servers it doesn't ask me for a password since i have key authentication setup.   I can also setup a script on one server to scp a file to another server and it just works without a password since i'm using key authentication.

---

### Post by SuaSwe on 2010-09-16
Sorry, I think I was unclear on one point there. :/ My private key is different for each server; only the passphrase is the same.

---

