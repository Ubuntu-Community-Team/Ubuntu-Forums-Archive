---
title: "sendmail: trusted-users or aliases?"
date: 2011-07-27
forum: General Help
---

### Post by kristo5747 on 2011-07-27
For a project that I have been assigned to, I need to send emails to a business partner (business_partner.com) from one production server. However, my emails neither reach their destination nor bounce back to me.

Working with our business partner's IT support, the following error was discovered in their maillogs:
> 
    chqsmt05 postfix/smtpd[1605]: NOQUEUE: reject: MAIL from unknown
    [hidden_ip_address]: 450 4.1.8 <ddwmadm@pxclpd30.hidden_domain_name.com>: Sender address rejected: Domain not found; 

from=<ddwmadm@pxclpd30.hidden_domain_name.com> proto=ESMTP helo=<pmempe31.prd.ext.hidden_domain_name.com>Further analysis by my IT support shows that emails are successfully sent out ("Message accepted for delivery"):

>   [root@hidden_host_name log]# grep -i business_partner maillog*
    maillog.1:May 13 17:41:18 hidden_host_name sendmail[23823]: p4DHfIet023823: to=me@hidden_domain_name.com,customer@business_partner.com, ctladdr=user_name (8116/6124), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=120260, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (p4DHfI53023824 Message accepted for delivery)The app I coded is not using a public internet email address (e.g. [EMAIL="me@hidden_domain_name.com"]me@hidden_domain_name.com[/EMAIL]) to send these notifications. Instead, it uses an intranet email address (the server's where my code resides: [EMAIL="user_name@servername.hidden_domain_name.com"]user_name@servername.hidden_domain_name.com[/EMAIL]). 

My IT support guys believe it is the cause of the problem. We created an alias but it made no change. Would adding my public internet email address to "trusted-users" file (we use sendmail) help? 

How can I solve this?  

Al.

---

