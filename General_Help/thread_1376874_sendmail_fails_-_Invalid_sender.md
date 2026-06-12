---
title: "sendmail fails - Invalid sender"
date: 2010-01-09
forum: General Help
---

### Post by drhex on 2010-01-09
Hi, I am trying to send email from my Ubuntu 9.10 (via git send-email) but sendmail is having problems delivering.

My ISP's has an outgoing mailserver, which I've added to /etc/mail/sendmail.cf:

**DSmailout.comhem.se**

and running "service sendmail restart" after that.

What happens when I try sending an email is that I get a mail back saying the mail was not delivered because of:

*Diagnostic-Code: SMTP; 550 Invalid sender <drhex@ganesha>*

Where "ganesha" is the name I gave my machine when I installed Ubuntu.
I can get a slightly more official hostname thru DHCP, and I've tried setting my hostname to that:

**hostname h83n2fls20o1047.bredband.comhem.se**

The only difference is that the error-mail I get back now says:
[I]
Diagnostic-Code: SMTP; 550 Invalid sender <drhex@h83n2fls20o1047.bredband.comhem.se>[/I]

I'm on a dynamic IP-adress and that hostname I got is apparently only known to my ISP rather than being put in a real DNS.

What more can I try to get mail thru to the outside world?

---

### Post by dcstar on 2010-01-10
> **drhex said:**
> Hi, I am trying to send email from my Ubuntu 9.10 (via git send-email) but sendmail is having problems delivering.

My ISP's has an outgoing mailserver, which I've added to /etc/mail/sendmail.cf:

**DSmailout.comhem.se**

and running "service sendmail restart" after that.

What happens when I try sending an email is that I get a mail back saying the mail was not delivered because of:

*Diagnostic-Code: SMTP; 550 Invalid sender <drhex@ganesha>*

Where "ganesha" is the name I gave my machine when I installed Ubuntu.
I can get a slightly more official hostname thru DHCP, and I've tried setting my hostname to that:

**hostname h83n2fls20o1047.bredband.comhem.se**

The only difference is that the error-mail I get back now says:
[I]
Diagnostic-Code: SMTP; 550 Invalid sender <drhex@h83n2fls20o1047.bredband.comhem.se>[/I]

I'm on a dynamic IP-adress and that hostname I got is apparently only known to my ISP rather than being put in a real DNS.

What more can I try to get mail thru to the outside world?

Assuming you have actually added that SMTP server to the correct Forwarders section, you ask your ISP why they are rejecting mail from you connection.

---

### Post by drhex on 2010-01-10
How does one choose which "forwarders section" the SMTP server is to be added to?

I can at least see that that "DS" line in sendmail.cf does make a difference:

With it, I get the "Invalid sender" described above.
Without it, there is a line in /var/log/mail.info ending with
[I]
stat=Deferred: Connection refused by alt4.gmail-smtp-in.l.google.com.[/I]

(I'm trying to send the email to a gmail account)

---

### Post by dcstar on 2010-01-12
> **drhex said:**
> 
..........
Without it, there is a line in /var/log/mail.info ending with
[I]
stat=Deferred: **Connection refused by alt4.gmail-smtp-in.l.google.com**.[/I]

(I'm trying to send the email to a gmail account)

Which means what it says: That mail server refused to a connection from your SMTP server.

I personally don't know why people don't just use the **postfix** package installed by default, it exists because it is so much simpler to set up than sendmail.

---

