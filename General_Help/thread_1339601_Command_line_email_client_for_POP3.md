---
title: "Command line email client for POP3"
date: 2009-11-27
forum: General Help
---

### Post by mikeunix on 2009-11-27
How do I configure a command line email client to send and receive IMAP or POP3.
I want to send email with something like:
mail -s "Test" -t "jo.bloggs@gmail.com" < message
so that this is sent from my POP3 or IMAP email account
And I want to be able to receive POP3 or IMAP email by using mail or just by looking in /var/spool/mail/username

If I was using a GUI email client, like evolution then all I would need to configure is SMTP server, POP3 or IMAP server and email account details.  Where do I configure this so that I can just use UNIX mail command and what packages do I need to install.

I don't think I need sendmail as I understand this is for setting up an email server and I want an email client.  I looked at fetchmail and getmail, but these seem to just receive mail and not send mail.

I also looked at mailutils, but I couldn't find any simple instructions to basically configure mail to send and receive POP3 or IMAP email.

Thanks

Mike

---

### Post by slumbergod on 2009-11-27
I posted instructions for configuring alpine (last?) year here in the forums under my current username so they'd be easy to find if I ever came back. Maybe they will help you. I found at the time there was no up-to-date info on setting them up. Alpine turned out to be easier than Mutt.

---

### Post by mikeunix on 2009-11-28
Thanks for this, but I am looking for a non-interactive program for sending and receiving email - I probably should have used the word "non-interactive" in original post, rather than just giving examples.  Alpine and Mutt are interactive screen based email programs.  I did install alpine and configured via your instructions and this worked first time for sending and receiving emails interactively, but doesn't seem to be any options to alpine to send and receive non-interactively.  So what I am looking for is simple instructions, exactly like you have given for configuring alpine, but for sending and receiving email non-interactively.  I THINK mailutils will do the job, but can't find any simple instructions to set it up.

---

