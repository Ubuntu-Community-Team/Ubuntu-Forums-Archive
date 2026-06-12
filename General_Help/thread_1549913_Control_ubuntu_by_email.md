---
title: "Control ubuntu by email?"
date: 2010-08-10
forum: General Help
---

### Post by PartisanEntity on 2010-08-10
Anyone know of a way to control ubuntu by email? I would like to close/launch applications for example. 

Thanks

---

### Post by nebu on 2010-08-10
check this out.... i had tried to make something like this myself..... but i had got bored!

[http://gcaldaemon.sourceforge.net/usage14.html](http://gcaldaemon.sourceforge.net/usage14.html)

---

### Post by elliotn on 2010-08-10
That sounds kul

---

### Post by PartisanEntity on 2010-08-10
wow thanks so much for this.

I have followed your guide, and now I am at the bit where you create a script, save it in the scripts folder, and then send yourself an email.

I created a script called: test.sh

In it I have: cd /home/me/

Then I send myself an email with test ls

(I want it to list the contents of my /home/me folder) but nothing is happening?

---

### Post by PartisanEntity on 2010-08-14
I still have not managed to get this to work. Here is the log file:

> 2010-08-14 12:00:09 | INFO  | Configurator   | GCALDaemon V1.0 beta 16 starting...
2010-08-14 12:00:09 | INFO  | Configurator   | RSS/ATOM feed converter enabled.
2010-08-14 12:00:09 | INFO  | Configurator   | Local time zone is Central European Time.
2010-08-14 12:00:09 | INFO  | HTTPListener   | HTTP server starting on port 9090...
2010-08-14 12:00:09 | WARN  | HTTPListener   | Set the 'http.allowed.hostnames' parameter to limit remote access.
2010-08-14 12:00:09 | INFO  | HTTPListener   | HTTP server started successfully.
2010-08-14 12:00:09 | INFO  | Configurator   | File listener disabled.
2010-08-14 12:00:09 | INFO  | Configurator   | LDAP server disabled.
2010-08-14 12:00:09 | INFO  | Configurator   | Gmail notifier disabled.
2010-08-14 12:00:09 | INFO  | Configurator   | Sendmail service disabled.
2010-08-14 12:00:09 | INFO  | MailTerminal   | Mailterm service started successfully.
2010-08-14 12:00:16 | WARN  | MailTerminal   | Unexpected mailterm error!


  [1 ] javax.mail.AuthenticationFailedException

  [2 ] at javax.mail.Service.connect(Service.java:306)

  [3 ] at javax.mail.Service.connect(Service.java:156)

  [4 ] at javax.mail.Service.connect(Service.java:105)

  [5 ] at org.gcaldaemon.core.GmailEntry.connectSMTP(GmailEntry.java:372)

  [6 ] at org.gcaldaemon.core.GmailEntry.connect(GmailEntry.java:152)

  [7 ] at org.gcaldaemon.core.GmailPool.borrow(GmailPool.java:9 8 )

  [8 ] at org.gcaldaemon.core.mailterm.MailTerminal.run(MailTerminal.java:173)

---

