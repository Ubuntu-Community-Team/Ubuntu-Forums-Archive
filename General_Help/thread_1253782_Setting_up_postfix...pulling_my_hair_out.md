---
title: "Setting up postfix...pulling my hair out"
date: 2009-08-30
forum: General Help
---

### Post by Jago6060 on 2009-08-30
Hi all.

I'm trying to get postfix set up so I can send command line email.  I've tried a bunch of configurations but none seem to work.  Is there anyone who can give me some tips or point me in the direction of a good HowTo?

Stats:
Ubuntu Server 9.04
postfix version 2.5.5

---

### Post by Zill on 2009-08-30
I have never configured postfix myself but this may help...

[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")

---

### Post by Bachstelze on 2009-08-30
If all you want is sending email from the command-line, do yourself a favor and use SSMTP instead of postfix. ;)

```
sudo apt-get install ssmtp
```

You can see for example the [FreeBSD]("http://www.freebsd.org/doc/en_US.ISO8859-1/books/handbook/outgoing-only.html") handbook for instructions to configure it.

(Of course, if you want to send mail directly - i.e. not using your ISP's SMtp server - you will have to use a full-fledged MTA like Postfix.)

---

### Post by Jago6060 on 2009-09-13
Ok, I've never really worked with postfix much, so I need a bit more help...

Here's what I'm trying to do...
Short term: Send an email to my gmail account from command line, and send a page to my cell phone via [*phone number*]@txt.att.net.

Long term: Send email/page alerts via Nagios to my email/cell phone.  Although I think this part will be easy once I can do it via command line.


Problem--I have postfix and mailx installed.  I issue the following command...
```
mail -s "Hello World" xxxxxxxxx@gmail.com
my message here
.

```
And it outputs...
```
You have new mail in /var/mail/root
```

I really have no idea how to set up any of the parameters in the postfix config.  I really need some basic basic basic help.  I haven't done any config on postfix or mailx thus far.

---

### Post by Jago6060 on 2009-09-13
Solved

---

### Post by Zill on 2009-09-13
> **Jago6060 said:**
> Solved
Rather than keeping the info to yourself it would be helpful to others who find this thread to show exactly *how* you solved the problem. ;-)

---

### Post by Jago6060 on 2009-09-13
> **Zill said:**
> Rather than keeping the info to yourself it would be helpful to others who find this thread to show exactly *how* you solved the problem. ;-)

Oh...right.  So here's what I did

```

sudo apt-get install postfix mailx
dpkg-reconfigure postfix

```
Screen 1: Select "Internet Site"
Screen 2: Type in the domain name, I just left mine as the prompt name(ubuntu-thin-client)
Screen 3: Type in "root"
Screen 4: Leave this blank because you don't want the box to accept mail for anywhere
Screen 5: Select "No"
Screen 6: Type 127.0.0.1/8
Screen 7(Mailbox Size Limit): Leave this as 0
Screen 8: Leave the default
Screen 9: Select "ipv4"


Done!

What this does:  In short, it allows you to send email from your command line to wherever it needs to go.  I used this method on Ubuntu 9.04 and have used to to send email as well as SMS messages via the email protocol.

---

### Post by Zill on 2009-09-13
Jago6060:  Thanks for that - it will help other users when they have a similar problem.

Glad you got it working. :-)

---

