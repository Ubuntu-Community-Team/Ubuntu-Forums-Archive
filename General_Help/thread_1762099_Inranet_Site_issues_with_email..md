---
title: "Inranet Site issues with email."
date: 2011-05-18
forum: General Help
---

### Post by garyeep on 2011-05-18
First off new to Ubuntu, so bare with me.  Ive set up lamp on Ubuntu Desktop version 11.04.  This computer will be hosting a Intranet website, so not outside hits or .com's needed.  Its set up with a static IP, our windows DNS servers points to it and everyone on the network can view the site great. (Joomla site).  However whatever we do we cannot get the email to work from the site.  Weve installed sendmail and other clients they dont seem to relay messages at all.  All i need is when a user sends a site via the email on Joomla it gets sent or relayed to the proper outside (exchange mostly) email address.  All the ports are open and firewall off on the Ubuntu box.  Config files seem to look ok however when you send an email through the terminal it says cannot connect to SMTP.  Someone was telling me that since Im on a intranet instead of internet that this is not going to happen correctly.  Thoughts?  I know this is vague but Im stumped and have never seen this.  On the site is says email sent, nothing receives to the senders. All the latest upgrades and patches are done as well.
Thank you for everyones time!

---

### Post by dcstar on 2011-05-19
> **garyeep said:**
> First off new to Ubuntu, so bare with me.  Ive set up lamp on Ubuntu Desktop version 11.04.  This computer will be hosting a Intranet website, so not outside hits or .com's needed.  Its set up with a static IP, our windows DNS servers points to it and everyone on the network can view the site great. (Joomla site).  However whatever we do we cannot get the email to work from the site.  Weve installed sendmail and other clients they dont seem to relay messages at all.  All i need is when a user sends a site via the email on Joomla it gets sent or relayed to the proper outside (exchange mostly) email address.  All the ports are open and firewall off on the Ubuntu box.  Config files seem to look ok however when you send an email through the terminal it says cannot connect to SMTP.  Someone was telling me that since Im on a intranet instead of internet that this is not going to happen correctly.  Thoughts?  I know this is vague but Im stumped and have never seen this.  On the site is says email sent, nothing receives to the senders. All the latest upgrades and patches are done as well.
Thank you for everyones time!

[LIST=1]
[*]Sendmail is not a "client, it is a MTA.
[*]Don't use complicated things like Sendmail, install **Postfix** and configure it as an Internet site.
[/LIST]

---

