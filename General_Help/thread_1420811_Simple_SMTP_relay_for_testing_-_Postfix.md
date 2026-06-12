---
title: "Simple SMTP relay for testing - Postfix?"
date: 2010-03-03
forum: General Help
---

### Post by thelaw on 2010-03-03
Greetings, Forum!

I am basically a user and not much of a linux-head.  Additionally, I am not that knowledgeable on mail servers.  With that said, I would like to post what I am trying to accomplish and to seek out some guidance on what the best way to do this is and, if possible, some assistance in doing so.

My scenario is thus: A VoIP system (namely Cisco), sends smtp notifications to users that they have a voicemail.  Occasionally, these things stop working and I have to figure out why.  Typically, all I do is enter an smtp server address (typcally Exchange or Groupwise) in a field on the VoiceMail server and hit save.

What I would like is to carry around on my laptop an small mail server that I could point this to for testing to verify things are working.  Then, when the customer upgrades, replaces, etc., their mail server, I can refer to a "known good" by using my laptop (currently running Kubuntu Hardy)

I've researched and located Postfix and xmail. Xmail failed on the install and Postfix seems like the choice as it looks to be somewhat native to Ubuntu.

I've installed and set it up as "local only" and pretty much left the rest as defaults.  I set the domain as "laptop.int"

I tried sending test message by doing: 

sendmail [email]postmaster@laptop.int[/email]
yada yada
.

Not sure what to do next, though.

All I would like is the ability to setup a test user that can receive these notifications and the ability to read the notification so I can determine if the basic functionality of the VoiceMessaging system notification is working.  Additionally, I'd need to do vlans other than the current subnet.  I don't really need to full blown mail server...or...do I?

Am I using the correct utility (Postfix)?  And how, on earth, does this get configured?

Here is the current configuration:

thelaw@laptop:~$ sudo dpkg-reconfigure postfix
 * Stopping Postfix Mail Transport Agent postfix                                                                                     [ OK ]
setting synchronous mail queue updates: false
setting myorigin
setting destinations: laptop.int, laptop, localhost.localdomain, localhost
setting relayhost:
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_size_limit: 100000
setting recipient_delimiter: +
setting inet_interfaces: loopback-only
setting default_transport: error
setting relay_transport: error
setting inet_protocols: all

Thanks!

---

