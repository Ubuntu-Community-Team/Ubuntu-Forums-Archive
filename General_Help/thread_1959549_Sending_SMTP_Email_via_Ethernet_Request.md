---
title: "Sending SMTP Email via Ethernet Request"
date: 2012-04-16
forum: General Help
---

### Post by chiques on 2012-04-16
Hello Everyone,

I am practicing using embedded systems. I would like to send an alarm email  using some sample code on the MCu. 

The problem is the functionality of these libraries (the code) is a bit old and does not clearly spell out how to handle the SMTP TLS security issue.

As a work around, I would like to set up my Ubuntu 11.04 box which has Thunderbird configured as an email client (Thunderbird can easily send emails to my Gmail account).

**Is there a command or utility which will allow the micro controller via my LAN to send an email message from my Ubuntu machine?** For example, my SMTP_SERVER=my_ubuntu_machine_ip and SEND_EMAIL=function_ubuntu_email().

I guess my Ubuntu box would be my proxy (please correct me if I'm wrong).

I don't even know if this even possible.

Thanks for any help.

---

### Post by dcstar on 2012-04-16
> **chiques said:**
> 

**Is there a command or utility which will allow the micro controller via my LAN to send an email message from my Ubuntu machine?** For example, my SMTP_SERVER=my_ubuntu_machine_ip and SEND_EMAIL=function_ubuntu_email().
.

```
man postfix
```

---

### Post by chiques on 2012-04-16
> **dcstar said:**
> ```
man postfix
```

Thanks!

---

