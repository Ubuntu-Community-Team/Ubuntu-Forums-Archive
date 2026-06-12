---
title: "Squirrel Mail Question"
date: 2011-04-09
forum: General Help
---

### Post by laus_deo on 2011-04-09
Well some background information. I'm just messing around with website hosting at the moment, I thought it would be fun to try out, and so far it has been. I have a Linux/Apache/MySQL/PHP system going on, and was trying to use the PHP mail() function until I found out it wouldn't send to exterior mail services (like yahoo/gmail), so I thought it might be fun to figure out how to host a email server myself. But I guess it would be nice to know if you can get the mail function to send the stuff to outside sites. 

I have Squirrel Mail working, and the PHP mail() function will send stuff to it, but I can't send/ receive emails from outsides sites. Part of it might be that I haven't purchased a domain name, would that be an issue? Any other advice would help too.

Thanks.

---

### Post by SeijiSensei on 2011-04-09
[http://ubuntuforums.org/showpost.php?p=10584000&postcount=2](http://ubuntuforums.org/showpost.php?p=10584000&postcount=2)

---

### Post by laus_deo on 2011-04-09
It's not timing out. So I dunno. I'm not sure if this would make a difference, but I'm using the internet at a Texas public university, so that might mean something?

---

### Post by SeijiSensei on 2011-04-09
Do you have Postfix installed?  The PHP mail() function expects to find a "mail transfer agent" like Postfix or sendmail which does the actual mail exchange.  mail() hands the message to the MTA which sends it along to its destination.  It sounds to me like you're not running Ubuntu Server which has all these packages as part of the default installation.  If you're running PHP on an ordinary Ubuntu installation, you'll need to install Postfix manually.  "sudo apt-get install postfix" ought to do it.

---

### Post by laus_deo on 2011-04-09
yeah, I have manually installed postfix as well as maildir and I can get the php mail() to send an email to root@localhost but I can't get either the mail() function or the squirrel mail to send to any outside address.

---

### Post by SeijiSensei on 2011-04-09
What does /var/log/mail.log show for such a failed attempt?

---

### Post by laus_deo on 2011-04-09
```
Apr  9 21:53:43 ubuntu postfix/smtpd[19987]: warning: ::1: address not listed for hostname ubuntu
Apr  9 21:53:43 ubuntu postfix/smtpd[19987]: connect from unknown[::1]
Apr  9 21:53:43 ubuntu postfix/smtpd[19987]: warning: Illegal address syntax from unknown[::1] in MAIL command: <brooks@76.78.174.68>
Apr  9 21:53:43 ubuntu postfix/smtpd[19987]: lost connection after MAIL from unknown[::1]
Apr  9 21:53:43 ubuntu postfix/smtpd[19987]: disconnect from unknown[::1]
```

---

### Post by SeijiSensei on 2011-04-09
```
brooks@76.78.174.68
```

The valid syntax for mail with an IP address rather than a domain name requires square brackets around the address:

```
brooks@[76.78.174.68]
```

Try that.  It may still not work if Postfix isn't configured to accept mail with that addressing format.  The address you gave looks to be a residential connection.  Is that your address?  If so, you need to tell Postfix to listen on your external IP address and accept mail for that address. By default, Postfix listens only on localhost (127.0.0.1).

You probably need to read some documentation.  This is a good starting point: [https://help.ubuntu.com/10.04/serverguide/C/email-services.html](https://help.ubuntu.com/10.04/serverguide/C/email-services.html)  Mail is a complicated service to set up, more complicated than providing web services.

---

### Post by laus_deo on 2011-04-09
Okay, I'll look more into that. Thanks for all the help you've provided.

---

