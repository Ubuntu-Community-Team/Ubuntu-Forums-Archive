---
title: "Any ideas on how to recieve exchange mail on Ubuntu Server?"
date: 2009-08-06
forum: General Help
---

### Post by z0mbi3 on 2009-08-06
I've got a server at work that I want to be to pickup e-mails and react to said e-mails. So basically if it recieves an e-mail that matches certain conditions a script gets fired off.

The bit that's an issue for me at the moment is that the email account I'll be using to do this runs on an exchange server, and I'm just not sure what to do in the way of a client on Ubuntu server to pick it up.

Has anyone got any ideas on what I should be looking at? Thanks in advance.

---

### Post by dcstar on 2009-08-07
> **z0mbi3 said:**
> I've got a server at work that I want to be to pickup e-mails and react to said e-mails. So basically if it recieves an e-mail that matches certain conditions a script gets fired off.

The bit that's an issue for me at the moment is that the email account I'll be using to do this runs on an exchange server, and I'm just not sure what to do in the way of a client on Ubuntu server to pick it up.

Has anyone got any ideas on what I should be looking at? Thanks in advance.

"Clients" do not run on servers, e-mail clients access servers to fetch e-mails.

If you have an Ubuntu e-mail server then simply get the Exchange server to forward the e-mails to the account on the Ubuntu server.

---

### Post by vladanian on 2009-08-07
If the Exchange server has imap access turned on, then you can grab the mail with an imap client running on your ubuntu server.

---

### Post by z0mbi3 on 2009-08-11
> **dcstar said:**
> "Clients" do not run on servers, e-mail clients access servers to fetch e-mails.

If you have an Ubuntu e-mail server then simply get the Exchange server to forward the e-mails to the account on the Ubuntu server.

I don't have an Ubuntu e-mail server, I want some sort of command line based e-mail client running on my Ubuntu Server that can pick up mails from an account on an the exchange server.

> **vladanian said:**
> If the Exchange server has imap access turned on, then you can grab the mail with an imap client running on your ubuntu server.

I'll check out the imap side, thanks.

---

