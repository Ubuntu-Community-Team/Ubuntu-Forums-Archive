---
title: "exim4 for a web server and spam filters"
date: 2010-01-14
forum: General Help
---

### Post by fozzyuw on 2010-01-14
Hi all,

I've been scouring Google results and searching the Ubuntu forums for details on setting up an exim4 mail server on my website servers.

The reason?  So I can send email via PHP scripts for things like confirmations or thank you messages.  Typical stuff.

So far, I've setup exim4 and successfully sent mail to my Gmail, Yahoo! and work accounts via the command line (using mailx) and through PHP scripts.

My issue right now is proper mail server configuration regarding email trust and spam filters.

My work spam filter is catching all emails being sent from our web servers.  Google and Yahoo! seem to let it through, but I have a feeling it's due to lower security settings.

Ideally, I want to make sure I configure my mail servers the best I can such that mail sent from it can be fairly well trusted and not trigger spam filters.

Here's what I've got so far:
-----------------------------

Web server running exim4 NAT'd behind a firewall.
Firewall allows all outgoing SMTP traffic on port 25 (traffic from the server to the outside).
exim4 config looks like this:
```
dc_eximconfig_configtype='internet'
dc_other_hostnames='web-serv.companydomain.com;mydomain.com'
dc_local_interfaces='127.0.0.1'
dc_readhost=''
dc_relay_domains=''
dc_minimaldns='false'
dc_relay_nets=''
dc_smarthost=''
CFILEMODE='644'
dc_use_split_config='false'
dc_hide_mailname=''
dc_mailname_in_oh='true'
dc_localdelevery='mail_spool'
```
* note, domain names have been changed

```
fozzyuw@web-serv:/$ hostname
web-serv
```

Email headers I get my Gmail account look like this:
```
Delivered-To: myaddress@gmail.com
Received: by 10.142.188.7 with SMTP id l7cs154831wff;
        Thu, 14 Jan 2010 09:23:22 -0800 (PST)
Received: by 10.231.125.28 with SMTP id w28mr1112570ibr.50.1263489801516;
        Thu, 14 Jan 2010 09:23:21 -0800 (PST)
Return-Path: <www-data@mydomain.com>
Received: from web-serv.companydomain.com ([xxx.xxx.xxx.xxx])
        by mx.google.com with ESMTP id 9si861733iwn.108.2010.01.14.09.23.21;
        Thu, 14 Jan 2010 09:23:21 -0800 (PST)
Received-SPF: neutral (google.com: xxx.xxx.xxx.xxx is neither permitted nor denied by best guess record for domain of www-data@mydomain.com) client-ip=xxx.xxx.xxx.xxx;
Authentication-Results: mx.google.com; spf=neutral (google.com: xxx.xxx.xxx.xxxis neither permitted nor denied by best guess record for domain of www-data@mydomain.com) smtp.mail=www-data@mydomain.com
Received: from www-data by web-serv.companydomain.com with local (Exim 4.69)
	(envelope-from <www-data@mydomain.com>)
	id 1NVTQw-0003E3-Nb; Thu, 14 Jan 2010 11:24:34 -0600
To: My Name <my.address@companydomain.com>,My Name <myaddress@gmail.com>
Subject: Test Email
From: Website Manager <webmanager@officalcompanydomain.com>
Date: Thu, 14 Jan 2010 11:24:34 -0600
Content-Type: text/plain; charset=iso-8859-1
Content-Transfer-Encoding: quoted-printable
Content-Disposition: inline
MIME-Version: 1.0
Message-Id: <E1NVTQw-0003E3-Nb@web-serv.companydomain.com>

My test email.

```

What I'm wondering is:
a) Do I need to open up the firewall to allow incoming SMTP traffic?  I'm wondering if other mail servers might be trying to verify authenticity by sending a message back to the server to see if it responds.

b) I don't know much about SPF.  Is this something I need to setup?  Are there any good tutorials on how to do it?

c) Our web server uses virtual hosting and will be hosting several of our companies websites.  I'm not sure if part of the problem with security is coming from not having MX records setup for one of the website domains it's hosting.

d) Our companies email servers are different and separate.  Emails sent from our web servers will be set to have From: and Reply-to: to our company email servers, not our web-servers.

----
All I'm trying to do is get our web servers to send email from our website so I can do confirmation emails and similar.  This seems to be setup and working.

However, I'm concerned about confirmation emails getting caught in spam filters because I don't have the mail server configured very well.  Headers are coming from different domain names, some of those domain names aren't using MX records, etc.

Also, I noticed that email gets sent as Apache's process name "www-data".  I'm not sure if there's away to change this or not.

Any help or links to help would be appreciated.

I'm a PHP programmer and website designer.  I'm a green when it comes to setting up mail servers and configuring them properly.

Cheers!
Fozzy

---

