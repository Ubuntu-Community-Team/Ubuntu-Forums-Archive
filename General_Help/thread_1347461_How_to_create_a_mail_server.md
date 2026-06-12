---
title: "How to create a mail server?"
date: 2009-12-06
forum: General Help
---

### Post by Sp322 on 2009-12-06
Please can someone give me a good tutorial, I followed flurdys but that isn't working!

:popcorn:

---

### Post by kellemes on 2009-12-06
[https://help.ubuntu.com/community/MailServer]("https://help.ubuntu.com/community/MailServer")

---

### Post by Sp322 on 2009-12-06
thanks im going through that now

---

### Post by Sp322 on 2009-12-06
Okay so I completed Postfix & Dovecot


Now i'm getting:


[01] 12/6 15:22:38   ~ Status: Opening connection for delivery...
[01] 12/6 15:22:38 --> Connecting socket [1] with 1 entries to [COLOR=Red]mail[/COLOR].[COLOR=Red]x[/COLOR].com Port:465
[00] 12/6 15:22:39 +OK Dovecot ready.
[00] 12/6 15:22:39 > USER [COLOR=Red]x[/COLOR]
[00] 12/6 15:22:39 +OK
[00] 12/6 15:22:39 > PASS ********
[00] 12/6 15:22:41 -ERR Authentication failed.
[00] 12/6 15:22:41 > QUIT 
[00] 12/6 15:22:42 +OK Logging out




Any idea?? :(



mail.log:

Dec  6 15:22:39 [COLOR=Red]x[/COLOR] dovecot: pop3-login: Aborted login (1 authentication attempts): user=<[COLOR=Red]x[/COLOR]>, method=PLAIN, rip=[COLOR=Red]x[/COLOR], lip=[COLOR=Red]x[/COLOR], TLS
Dec  6 15:22:39 [COLOR=Red]x[/COLOR] dovecot: pop3-login: Aborted login (1 authentication attempts): user=<[COLOR=Red]x[/COLOR]>, method=PLAIN, rip=[COLOR=Red]x[/COLOR], lip=[COLOR=Red]x[/COLOR], TLS

---

### Post by Sp322 on 2009-12-06
Anyone, please help me! :( I keep getting errors every method I try so I thought I could try and get some help here

---

### Post by Sp322 on 2009-12-06
Im not getting that error anymore but now I get:




-ERR [IN-USE] Couldn't open INBOX: Internal error occurred. Refer to server log for more information

---

### Post by Sp322 on 2009-12-06
I just removed this line from dovecot.conf:

[COLOR=Red]default_mail_env = maildir:~/Maildir (for maildir)[/COLOR]


and now it isn't bringing me errors it just does this:


[COLOR=Red][01] 12/6 16:08:39   ~ Status: Opening connection for delivery...
[01] 12/6 16:08:39 --> Connecting socket [1] with 1 entries to x.x.com Port:465
[00] 12/6 16:08:40 +OK Dovecot ready.
[00] 12/6 16:08:40 > USER x
[00] 12/6 16:08:40 +OK
[00] 12/6 16:08:40 > PASS ********
[00] 12/6 16:08:40 +OK Logged in.
[00] 12/6 16:08:40 > QUIT 
[00] 12/6 16:08:40 +OK Logging out.
[00] 12/6 16:08:49   ~ Status: Canceling process...
[00] 12/6 16:08:49   ~ Status: Asking socket #1 to QUIT...
[00] 12/6 16:08:49   ~ Status: [-]
[00] 12/6 16:08:49   ~ Status: Closing all streams
[00] 12/6 16:08:49   ~ Status: Creating report...
[00] 12/6 16:08:49   ~ Status: [-]
[00] 12/6 16:08:49   ~ Status: Closing all streams
[00] 12/6 16:08:49   ~ Status: Finishing...
[/COLOR]

---

