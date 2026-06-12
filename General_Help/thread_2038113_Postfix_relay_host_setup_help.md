---
title: "Postfix relay host setup help"
date: 2012-08-05
forum: General Help
---

### Post by cwhite3424 on 2012-08-05
I'm currently implementing eGroupware's collaboration software and need some help setting up an email server. I'm running Ubuntu 10.04 LTS server (non GUI) and have eGroupware running fine except for email services. The details of my email setup are:

[LIST=1]
[*]There is no Internet domain associated with my server
[*]All outside email is sent and received via ISP
[*]Mail is retrieved from ISP POP3 via fetchmail and put in local directories for delivery by Dovecot via IMAP
[*]eGroupware's email client is connecting to Dovecot via IMAP to retrieve mail fine
[*]I would also like to create some "internal" email accounts for  interoffice messaging i.e. not able to receive or send to Internet  addresses
[*]eGroupware's email client needs a local SMTP server to relay mail to the ISP's SMTP server and deliver "internal" emails
[/LIST]
I need help with Postfix setup. I've tried several different permutations and none have been able to deliver either local or Internet emails.:( Any help would be appreciated!

Chuck White

---

### Post by dcstar on 2012-08-06
> **cwhite3424 said:**
> 
[LIST=1]
[*]...
[*]...
[*]...
[*]...
[*]I would also like to create some "internal" email accounts for  interoffice messaging i.e. not able to receive or send to Internet  addresses
[*]eGroupware's email client needs a local SMTP server to relay mail to the ISP's SMTP server and deliver "internal" emails
[/LIST]
I need help with Postfix setup. I've tried several different permutations and none have been able to deliver either local or Internet emails.:( Any help would be appreciated!


[LIST=1]
[*]```
sudo dpkg-reconfigure postfix
``` Select "Internet"


[*]Create local Linux accounts for whatever users you need.
[/LIST]

---

