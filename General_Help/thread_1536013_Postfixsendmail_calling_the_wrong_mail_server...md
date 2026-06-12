---
title: "Postfix/sendmail calling the wrong mail server.."
date: 2010-07-21
forum: General Help
---

### Post by sp0nge on 2010-07-21
Hello, 

I am having a terrible time figuring this out, any input will be appreciated. I have a machine running postfix on which I'm using the mail command to send log files to a central server. However, I'm seeing firewall log entries which indicate a totally different mail server is being called! I have reviewed the .cf files in /etc/postfix thinking one would be the answer, but that doesn't appear to be the case. Please help me understand what I'm missing!

Thanks in advance for your help and insight.

---

### Post by dcstar on 2010-07-22
> **sp0nge said:**
> Hello, 

I am having a terrible time figuring this out, any input will be appreciated. I have a machine running postfix on which I'm using the mail command to send log files to a central server. However, I'm seeing firewall log entries which indicate a totally different mail server is being called! I have reviewed the .cf files in /etc/postfix thinking one would be the answer, but that doesn't appear to be the case. Please help me understand what I'm missing!


Mail is sent to the IP address of whatever MX record exists for the domain you are sending to.

Read up on how the SMTP protocol works and then you may understand a bit better.

---

