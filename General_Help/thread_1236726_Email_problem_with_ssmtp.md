---
title: "Email problem with ssmtp?"
date: 2009-08-10
forum: General Help
---

### Post by Snowhog on 2009-08-10
Not because I need to, but because I want to.

I've installed fetchmail, ssmtp, and mutt.

I've configured the /etc/ssmtp/ssmtp.conf file.

I've written the .fetchmailrc and .muttrc files.

I can compose and send mail with mutt no problem. When I attempt to fetchmail, I get:

2 messages for [email]xxxxxxx@myisp.net[/email] at smtp.myisp.net (26064 octets).
reading message [email]xxxxxxx@myisp.net@mail.myisp.everyone.net[/email]:1 of 2 (25328 octets).[B]ssmtp: No recipients supplied - mail will not be sent
..fetchmail: error writing message text
fetchmail: MDA error while fetching from [email]xxxxxxx@myisp.net@smtp.myisp.net[/email]
fetchmail: Query status=6 (IOERR)[/B]

[email]xxxxxxx@myisp.net[/email], smtp.myisp.net, and [email]xxxxxxx@myisp.net@mail.myisp.everyone.net[/email] above aren't the 'real' entries - I've changed them here for privacy.

What am I missing? What do I need to do so that I can retrieve my email from my account on my ISP?

Thank you.

---

### Post by andrew.46 on 2009-08-10
Hi Snowhog,

I have written a guide that uses similar applications except that I use msmtp instead of ssmtp (which actually might serve you better anyway?). Perhaps if you have a look over the configuration I demonstrate for fetchmail/msmtp/procmail/mutt you might be able to extract a few clues about your own problem?

[Howto] Use Mutt with Gmail
[http://ubuntuforums.org/showthread.php?t=1021746](http://ubuntuforums.org/showthread.php?t=1021746)

Just ignore all the gmail/certs stuff :-). If this is no help to you I will gladly see if I can cast any light on your existing setup.

Andrew

---

### Post by Snowhog on 2009-08-10
Thank you for the reply. I got it figured out.

I had mistakenly thought I didn't need a MDA (Mail Delivery Agent), and so hadn't installed one. Realizing my error, I installed procmail and wrote the .procmailrc file and all is well.

---

