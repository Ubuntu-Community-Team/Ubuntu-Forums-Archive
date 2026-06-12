---
title: "Get mail by POP3, serve by IMAP, solutions?"
date: 2011-02-16
forum: General Help
---

### Post by H4rm0ny on 2011-02-16
I'm just wondering if a solution to this already exists somewhere and I just don't know about it. I expect it does.

I want to retrieve emails from my POP3 servers to my home server. But from there, I want to be able to access them via IMAP from my other computers, i.e. desktop, laptop, phone. And then of course I want to be able to send emails from said devices via IMAP to my home server which POP3's them out to my mail servers.

Basically, I have a few POP3 accounts with various hosts and I want to conveniently interact with them from lots of devices using my preferred software (i.e. Mutt, or Thunderbird on my Windows boxes). My home server is Ubuntu Server if that's relevant.

Any easy way to do this?

Many thanks,

H.

---

### Post by kerry_s on 2011-02-16
i use gmail to pop all my mail, so i only have to check gmail.
gmail also has imap.

---

### Post by ianc1 on 2011-02-16
Is there an option to get them via IMAP from your ISP or however provides the email?  To me this would seem a better idea, I do this and then access there servers from all devices and also store copies on all devices to save downloading them every time.

---

### Post by H4rm0ny on 2011-02-16
Thanks for both replies. I'm definitely fixed on what I want to do: Create a home IMAP server and import my mails via POP3 to it. There are a lot of reasons why I want to do this. They range from needing to GPG sign some of my emails, liking using my own email clients, back up procedures to privacy concerns (i.e. not letting Google near them). There is an option to get them via IMAP from a couple of the mail providers I use, but this needs to be a long-term solution and I'll probably exceed the limits on my mail accounts.

---

### Post by srs5694 on 2011-02-16
Look into [Fetchmail,](http://fetchmail.berlios.de/) which retrieves mail via POP, IMAP, or various other protocols for injection into a local mail queue. You can then run whatever IMAP server you like to deliver the mail on your local network. Personally, I use [Dovecot,](http://www.dovecot.org/) but there are lots of other options.

For sending mail, neither POP nor IMAP is the correct protocol; you must use SMTP for that. IIRC, [Postfix](http://www.postfix.org) is the default SMTP server for Ubuntu, but I might not be remembering correctly. Others, such as sendmail, qmail, and Exim, are available and will work as well. You'll probably need an SMTP server running to accept the output from Fetchmail, too, so using one for your outgoing mail won't add much to the complexity of the setup.

---

### Post by psusi on 2011-02-16
I've also been using fetchmail/dovecot/dovecot-postfix for years and have been quite happy.

---

### Post by H4rm0ny on 2011-02-18
Thanks for all the replies. **srs5694** and **psusi** in particular, your suggestions got me started on the right trail. From there, I discovered this *enormously* helpful How To which pretty much details everything I'm after.

[https://help.ubuntu.com/community/POP3Aggregator]("https://help.ubuntu.com/community/POP3Aggregator")

I've now set up Dovecot on my home server which provides me with an IMAP service. And I'm using GetMail to grab my emails by POP3 and populate the mail files that Dovecot serves to my client devices.

It's actually taking me longer to convert and import my Thunderbird mbox files to MailDir on the new server, than it has been to set all this up. This is going to be really useful. Thanks all,

Harmony.

---

### Post by oube on 2013-04-17
H4rm0ny, I am recently looking for the same thing, setting up my own fetch, imap, then convert and import my thunderbird mails, just like yours. Do you have an outline of what you did to bring this setup up and running? Also, do you have to setup DNS for your home server to use a imap client or did you use web client?

Just a question on the side, why the choice of GetMail instead of fetchmail?

---

### Post by overdrank on 2013-04-17
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/misc.php?do=showrules")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

