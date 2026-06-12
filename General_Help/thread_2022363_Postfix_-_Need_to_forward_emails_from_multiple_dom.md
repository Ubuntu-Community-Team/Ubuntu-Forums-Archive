---
title: "Postfix - Need to forward emails from multiple domains to 1 domain."
date: 2012-07-10
forum: General Help
---

### Post by rabidsloth on 2012-07-10
So, we have 1 primary email domain for our company, call it @primaryemail.com. We also have about 50 other domains that all of our users need to be able to receive email from. What I'm trying to figure out, is if we can setup a postfix server, point all of the secondary domains to that, and have it automatically forward email to [EMAIL="whateveruser@primaryemail.com"]whateveruser@primaryemail.com[/EMAIL]..

Example: Emails going to [EMAIL="bob@secondaryemail.com"]bob@secondaryemail.com[/EMAIL] or [EMAIL="sandy@someotheremail.com"]sandy@someotheremail.com[/EMAIL] should be received by the postfix server, and then automatically forwarded to [EMAIL="bob@primaryemail.com"]bob@primaryemail.com[/EMAIL] or [EMAIL="sandy@primaryemail.com"]sandy@primaryemail.com[/EMAIL].

Anyone have any ideas on how we could accomplish this using postfix?

---

### Post by SeijiSensei on 2012-07-10
The problem is pretty simple if the users have the same username on all the domains.  You'd just set up a bunch of aliases in /etc/aliases, one for each user, that points all mail for "bob" to "bob@primaryemail.com".  Then give postfix the list of domains for which it handles final delivery.

I use sendmail and could set this up in a few minutes.  The domains go into a file (called /etc/mail/local-host-names on my CentOS server), and the aliases go into /etc/aliases.  

Things become more complicated if there's another "bob" in a different domain that needs to be forwarded to a different account in primaryemail.com.  Then you need aliases that include a domain part as well as a username.  I know how to do that in sendmail, too, by setting up a "virtusertable" database.  I don't know about postfix.

Since you're going to be pushing all this mail through the Linux box, perhaps you want to install spam and virus scanning software on the box as well?  I use [MailScanner]("http://www.mailscanner.info/"), an incredibly powerful and flexible scanner.  It invokes SpamAssassin and your choice of AV scanner(s).  I use ClamAV.

---

### Post by rabidsloth on 2012-07-11
Awesome! I was able to get this working with sendmail in no time at all. Thanks!

---

