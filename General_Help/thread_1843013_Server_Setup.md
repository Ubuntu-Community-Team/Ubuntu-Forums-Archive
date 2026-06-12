---
title: "Server Setup"
date: 2011-09-12
forum: General Help
---

### Post by Urie on 2011-09-12
ok so i have been using ubuntu for about 4-5 months (desktop) and im going to use it for my business

Im looking into getting a server but is there any software that i can use for e-mail calendar and contacts for users thts easy to install since im pretty new to all this

CHris

---

### Post by Dangertux on 2011-09-12
Are you talking about using Ubuntu server as an alternative to say Windows SBS? To deal with local domain issues?

If that is what you are talking about check out the following

For domain
----------------
OpenLDAP
Samba 4
Bind (I keep editing this in and out...it's kind of supplementary and not a one shot one kill application, be aware you will likely end up using this in conjunction with OpenLDAP)

For email 
--------------
Postfix
sendmail (note this does NOT meet the easy requirement)
squirrel mail


Or are you talking about setting it up on the employees workstations? To work on a Windows network? If that's the case your client applications should work just fine with a Windows server.

---

### Post by haqking on 2011-09-12
> **Dangertux said:**
> Are you talking about using Ubuntu server as an alternative to say Windows SBS? To deal with local domain issues?

If that is what you are talking about check out the following

For domain
----------------
OpenLDAP
Samba 4

For email 
--------------
Postfix
sendmail (note this does NOT meet the easy requirement)
squirrel mail


Or are you talking about setting it up on the employees workstations? To work on a Windows network? If that's the case your client applications should work just fine with a Windows server.

+1

Remember that most email servers out there on the net are *nix based anyways so all local client apps work 99.9% of the time seemlessly regardless of OS.

If you mean desktop versions as you will be changing the users over to Linux then Evolution and Thunderbird work very well.

If you mean set up a Linux server for email than as Dangertux mentioned should be good.  And the windows clients (outlook) etc will deal with it relatively seamlessly.

---

### Post by drdos2006 on 2011-09-12
For a business server I would recommend Zentyal, does not need the latest and greatest hardware, easy for novices to set up, lots of on-line tutorials. 
For e-mail, calendar and contacts you are looking for egroupware. There are a few different flavours, such as "egroupware",  "FengGroupware" and Zentyal installs "Zarafa".

Zentyal uses web-based interface.

regards

---

### Post by linux2001 on 2011-09-13
Egroupware Online Collaboration Tool, is opensource program that use
openldap
postfix

[http://www.egroupware.org/]("http://www.egroupware.org/")

---

