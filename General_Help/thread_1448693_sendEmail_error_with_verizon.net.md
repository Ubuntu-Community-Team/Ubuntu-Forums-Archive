---
title: "sendEmail error with verizon.net"
date: 2010-04-06
forum: General Help
---

### Post by kaibob on 2010-04-06
I have been trying to use the sendEmail utility without success. I have copied the command and the resulting error message below. I have replaced email addresses and password with *** but I have double and triple checked them in the actual command line to insure that they are correct.

```
sendEmail -f ***@verizon.net -t ***@usa.com -u "Message title" -m "The body of the message" -s outgoing.verizon.net -xu *** -xp ***
Apr 06 20:00:52 dell sendEmail[4364]: ERROR => Received: 	500 5.5.1 Unknown command "" specified
```

I have appended various ports (including :25) to outgoing.verizon.net but that doesn't help. 

I ran the above command with the -vvv option and got the following. Everything is fine until the third line from the bottom. 

```
$ sendEmail -vvv -f ***@verizon.net -t ***@usa.com -u "Message title" -m "The body of the message" -s outgoing.verizon.net -xu *** -xp ***
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => Connecting to outgoing.verizon.net:25
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => My IP address is: 192.168.1.3
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => evalSMTPresponse() - Checking for SMTP success or error status in the message: 220 vms173011pub.verizon.net -- Server ESMTP (Sun Java(tm) System Messaging Server 7u2-7.02 32bit (built Apr 16 2009))
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => evalSMTPresponse() - Found SMTP success code: 220
Apr 06 20:03:31 dell sendEmail[4393]: SUCCESS => Received: 	220 vms173011pub.verizon.net -- Server ESMTP (Sun Java(tm) System Messaging Server 7u2-7.02 32bit (built Apr 16 2009))
Apr 06 20:03:31 dell sendEmail[4393]: INFO => Sending: 	EHLO dell
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => evalSMTPresponse() - Checking for SMTP success or error status in the message: 250-vms173011pub.verizon.net, 250-8BITMIME, 250-PIPELINING, 250-CHUNKING, 250-DSN, 250-ENHANCEDSTATUSCODES, 250-HELP, 250-XLOOP BB350E50FA14E756DE6BD3D78A032E20, 250-AUTH PLAIN LOGIN, 250-AUTH=LOGIN PLAIN, 250-ETRN, 250-NO-SOLICITING, 250 SIZE 20971520
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => evalSMTPresponse() - Found SMTP success code: 250
Apr 06 20:03:31 dell sendEmail[4393]: SUCCESS => Received: 	250-vms173011pub.verizon.net, 250-8BITMIME, 250-PIPELINING, 250-CHUNKING, 250-DSN, 250-ENHANCEDSTATUSCODES, 250-HELP, 250-XLOOP BB350E50FA14E756DE6BD3D78A032E20, 250-AUTH PLAIN LOGIN, 250-AUTH=LOGIN PLAIN, 250-ETRN, 250-NO-SOLICITING, 250 SIZE 20971520
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => The remote SMTP server does NOT support TLS :(
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => SMTP-AUTH: Using PLAIN authentication method
Apr 06 20:03:31 dell sendEmail[4393]: INFO => Sending: 	AUTH PLAIN Ym9iMjE1OQBib2IyMTU5AHR1dDcxNA==
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => evalSMTPresponse() - Checking for SMTP success or error status in the message: 235 2.7.0 PLAIN authentication successful.
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => evalSMTPresponse() - Found SMTP success code: 235
Apr 06 20:03:31 dell sendEmail[4393]: SUCCESS => Received: 	235 2.7.0 PLAIN authentication successful.
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => User authentication was successful
Apr 06 20:03:31 dell sendEmail[4393]: INFO => Sending: 	MAIL FROM:<***@verizon.net>
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => evalSMTPresponse() - Checking for SMTP success or error status in the message: 500 5.5.1 Unknown command "" specified
Apr 06 20:03:31 dell sendEmail[4393]: DEBUG => evalSMTPresponse() - Found SMTP error code: 500
Apr 06 20:03:31 dell sendEmail[4393]: ERROR => Received: 	500 5.5.1 Unknown command "" specified
```

Anyone know what's going on?

---

### Post by kaibob on 2010-04-06
I spent a little more time with google and found a bug report and a fix:

[https://bugs.launchpad.net/ubuntu/+source/sendemail/+bug/405733](https://bugs.launchpad.net/ubuntu/+source/sendemail/+bug/405733)

There is a new version of sendEmail, which works fine without modification, at

[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

---

