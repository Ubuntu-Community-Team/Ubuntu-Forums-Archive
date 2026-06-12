---
title: "How to send mail via terminal"
date: 2010-06-22
forum: General Help
---

### Post by Praveen30 on 2010-06-22
i know for this i have to install some package.i have installed this and write in my terminal this--

mail -s "mesage" <name@domain.com>

after executing this it ask for the CC..I have given the address.after hitting Enter it just go the new line with just blinking cursor so i have pressed ctrl+d for coming out of this and go to my previous home directory. i  checked my mail and there was nothing .Where i am going wrong?

---

### Post by -jo- on 2010-06-22
I am not sure if that will help, and if it's the same like when connecting with telnet to smtp. But try on an empty line a . (dot) and then enter.

---

### Post by arrange on 2010-06-22
You can use [sendEmail]("http://caspian.dotconf.net/menu/Software/SendEmail/"), it's very easy to use.
```
sendEmail -f arrange@centrum.cz -t ubuntu@ubuntu.com -u "SPAM: hello" -m "It's me." -s smtp.google.com -a /home/arrange/bulky_picture.bmp
```

---

### Post by dcstar on 2010-06-22
> **Praveen30 said:**
> i know for this i have to install some package.i have installed this and write in my terminal this--

mail -s "mesage" <name@domain.com>

after executing this it ask for the CC..I have given the address.after hitting Enter it just go the new line with just blinking cursor so i have pressed ctrl+d for coming out of this and go to my previous home directory. i  checked my mail and there was nothing .Where i am going wrong?

Press <Enter> to send it.
```
man mailx
```

---

### Post by Praveen30 on 2010-06-22
> **-jo- said:**
> I am not sure if that will help, and if it's the same like when connecting with telnet to smtp. But try on an empty line a . (dot) and then enter.

I have just checked it.Looks fine in terminal and no error is coming but nothing is coming in the mail.

---

### Post by Praveen30 on 2010-06-22
> **dcstar said:**
> Press <Enter> to send it.
```
man mailx
```

ya i know this mailx.if i am pressing enter without written anything then a new blank line is coming.in short,it is not working.

---

### Post by jerome1232 on 2010-06-22
like this
```
mail root@localhost
Cc: 
Subject: Terminal background is pretty cool, where did you get it?
All in the subject!
jeremy@main:~$ mail
"/var/mail/jeremy": 1 message 1 new
>N   1 Jeremy Jones       Tue Jun 22 07:14  15/590   Terminal background is pr
? 1
Return-path: <jeremy@main.homelinux.net>
Envelope-to: root@localhost
Delivery-date: Tue, 22 Jun 2010 07:14:14 -0700
Received: from jeremy by main.gateway.2wire.net with local (Exim 4.71)
	(envelope-from <jeremy@main.homelinux.net>)
	id 1OR4Ev-0001pW-V1
	for root@localhost; Tue, 22 Jun 2010 07:14:14 -0700
Date: Tue, 22 Jun 2010 07:14:13 -0700
Message-Id: <E1OR4Ev-0001pW-V1@main.gateway.2wire.net>
To: <root@localhost>
Subject: Terminal background is pretty cool, where did you get it?
X-Mailer: mail (GNU Mailutils 2.1)
From: Jeremy Jones <jeremy@main.homelinux.net>

All in the subject!
? q
Saved 1 message in /home/jeremy/mbox
Held 0 messages in /var/mail/jeremy

```


But I think your problem is you don't have a service running to deliver the mail. Do you have exim or postfix running? if Memory serves they are not installed on desktop systems by default. I had to add it and manually change permissions on my mailbox to get it working a few weeks ago.

---

### Post by Praveen30 on 2010-06-22
how can i get to know these services running or not?

---

### Post by andriansah on 2011-04-16
> **Praveen30 said:**
> how can i get to know these services running or not?

sudo service name-ofservice status

---

### Post by ultner on 2012-04-20
the error when doing

```
mail -s "SUBJECT" <to>
```is, that mail want some message. a possible solution is to implement

```
echo "some message to send" | mail -s "SUBJECT" <to>
```~markus

---

### Post by Habitual on 2012-04-20
easiest way ever...
echo TEST| mail [email]user@domain.com[/email]

---

### Post by oldos2er on 2012-04-20
Old thread closed.

---

