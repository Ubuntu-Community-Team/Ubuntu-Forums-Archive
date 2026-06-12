---
title: "Advice on local mail server to retreive mail from ISP"
date: 2012-10-09
forum: General Help
---

### Post by greavette on 2012-10-09
Hello,

We are a small company where our mail address is through our ISP.  We've had this mail address a long time and we don't want to change it.  But we want to have our mail stored locally on our own servers.  Therefore our requirements are:

Retrieve mail from our ISP and store this mail locally.  On this local mail server we would set-up our own folders in which to store our mail.
Use only a webmail client for managing mail.  Webmail client would connect to local mail server using IMAP.
Webmail client would have a shared (global) addressbook and mailinglist.  We don't want an LDAP addressbook.  Contacts will be administered through the webmail client. 
Mail would be sent through the ISP (or through the local mail server which points to the ISP SMTP server).
The two webmail clients we would prefer to use are either egroupware's or roundcube.  I've used Citadel mail server.  It's an amazing email server that satisfies almost all of our requirements except that Roundcube and egroupware won't work with IMAP to Citadel.  The webmail client doesn't have to be egroupware or Roundcube, but it has to look something like these.
We use Zentyal as our Domain Controller.  Would like to have this email server use our Domain Controller for user login.
Must run on Ubuntu (Server 12.04)

So, what would be our best option.  Should we install postfix with dovecote on Ubuntu Server and load up Roundcube or egroupware to solve our requirements?  Or can someone suggest another option for us.  Should I use Zimbra or Horde or Zarafa instead.  Whatever the solution we'll be installing this mail server on Ubuntu Server in a VM so resources aren't an issue for us.

Any advice you can provide would be appreciated.

---

### Post by TheFu on 2012-10-09
Ok, you have lots of requirements. Most do not require an all-in-one solution.
* postfix for SMTP
* whatever mail client you want
* whatever IMAP server you want
* fetchmail to pull the email from the ISP to the local server and shove it into the inbox you want

Or you could setup .forwards from your ISP to automatically forward emails to your server
Or you could setup primary and secondary MX records with your DNS provider and make the ISP MX the secondary with your local server as the primary.

I've been running Zimbra servers for a few years. They are nice, but hardly perfect.  If we didn't need "enterprise calendaring", I'd drop back to standalone postfix, dovecot and whatever webmail the rest of the company wanted.  Last time I checked, Zimbra didn't work on 12.04 yet, but it has been a few months.

I'd also recommend a front-end spam server that can cache inbound email when you need a few hours to work on the real email server back-end. Your ISP server can perform that role too, but having a dedicated spam/AV server is a big help.

---

### Post by greavette on 2012-10-09
Thanks.   I was hoping for more of an all in one solution...these separate tools all being used for my solution sound so complicated to setup and administer.  I'd rather not have to devote a lot of time administering various products.  This is why it's really too bad that citadel doesn't quite work for us.  It's an awesome and easy to use mail server...very underrated.  But the whole room thing to handle contacts and mailing lists and it not working with Roundcube was a huge show stopper for us.

I think I'll have to give these seperate products a go and see how it goes.  I don't quite understand how we administer folders and user access yet.  Do we do this all from the webmail frontend?  I've got a lot to learn.

I've found these blogs and will start with these to give it a go:

[http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/](http://www.exratione.com/2012/05/a-mailserver-on-ubuntu-1204-postfix-dovecot-mysql/)

or 

[http://ubuntuguide.org/wiki/Mail_Server_setup](http://ubuntuguide.org/wiki/Mail_Server_setup)

If anyone else wants to add their two cents, I'm all ears.

---

### Post by collisionystm on 2012-10-09
Zentyal.

wwww.zentyal.com

---

### Post by greavette on 2012-10-09
If you mean Zarafa with Zentyal...doesn't Zarafa only use ldap with their global addressbook where from within my webmail client I woudn't be able to administer my contacts.  I'd have to use another tool to add/update my contacts in the ldap?

---

### Post by TheFu on 2012-10-09
After using a packaged setup from Zimbra, I miss the days of being able to maintain east F/LOSS package individually.  Upgrades for the 20-ish tools used by Zimbra usually means swapping in a new VM instead of 10 minutes of apt-get work.  It is a bigger deal every 6-12 months, instead of smaller patches as they become available. 

That's another reason to have a front-end email server .... so you don't leave an unpatched service running on the open internet to be cracked.

---

