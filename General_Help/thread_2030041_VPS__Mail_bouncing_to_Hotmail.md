---
title: "VPS | Mail bouncing to Hotmail"
date: 2012-07-20
forum: General Help
---

### Post by matimont on 2012-07-20
Hi, 



Whenever I want to send an email to hotmail I get this (xx.xx.xx.xx is my ip address)
  host mx2.hotmail.com[65.54.188.110] said: 550 DY-001     (BAY0-MC3-F6) Unfortunately, messages from xx.xx.xx.xx weren't sent.     Please contact your Internet service provider. You can tell them that     Hotmail does not relay dynamically-assigned IP ranges. You can also refer     your provider to [http://mail.live.com/mail/troubleshooting.aspx#errors](http://mail.live.com/mail/troubleshooting.aspx#errors). (in     reply to MAIL FROM command)
  

What may be the reason? I can receive mails ok and send to gmail for example with no issues...


When I went to mxtoolbox, I checked with the backlist and all are ok..
  Now, I ran a SMTP check and got this: "Reverse DNS FAILED! This is a problem"
  I think there's some setting I need to configure in Webmin or Virtualmin?

---

### Post by Habitual on 2012-07-20
You  ideally should have the "Reverse DNS" set on xx.xx.xx.ip to point at the domain.

It is NOT a "webmin or Virtualmin" setting.

---

### Post by dcstar on 2012-07-23
> **matimont said:**
> Hi, 



Whenever I want to send an email to hotmail I get this (xx.xx.xx.xx is my ip address)
  host mx2.hotmail.com[65.54.188.110] said: 550 DY-001     (BAY0-MC3-F6) Unfortunately, messages from xx.xx.xx.xx weren't sent.     Please contact your Internet service provider. You can tell them that     **Hotmail does not relay dynamically-assigned IP ranges.** You can also refer     your provider to [http://mail.live.com/mail/troubleshooting.aspx#errors](http://mail.live.com/mail/troubleshooting.aspx#errors). (in     reply to MAIL FROM command)
  

What may be the reason? I can receive mails ok and send to gmail for example with no issues...
.......

The reason seems pretty clear.

---

### Post by proffesionalx on 2012-11-03
So did you find a solution to your problem? Gmail seems to accept mail  but aol, hotmail and the rest seem to reject it...

---

