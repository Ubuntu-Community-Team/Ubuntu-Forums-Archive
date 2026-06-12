---
title: "IMAP Download - Filter - Redirect"
date: 2009-08-17
forum: General Help
---

### Post by mihamil on 2009-08-17
I have a school email address that I have never used because it has been blasted with spam almost uncontrollably since I was assigned the address (no idea why).  More teachers in my school are starting to not accept other email addresses.  They always want to use your .edu assigned address.  I do have IMAP access to this account.  Is it possible for me to set up some kind of automated setup to download messages and forward all emails from one specific domain to another account on my own server.  I currently have my own mail server set up in postfix that I use for my primary email account.  If it could download all mail and deliver only those that are from addresses at myschoolhere.edu to my own mailbox on my server I wouldn't have to deal with checking this account and sifting through several hundred emails per week.  Any ideas?

---

### Post by mihamil on 2009-08-18
I figured out how to pull the emails using fetchmail, but how can I configure it to discard anything that is not from myschoolhere.edu.  I basically want to whitelist myschoolhere.edu and blacklist everything else coming from this source.

---

### Post by mihamil on 2009-08-18
OK.  I think I am on to something but still need a little bit of help.  I am using fetchmail which downloads it from the schools mail server and pushes it towards my mailbox.  I set up two rules on SpamAssassin.  The first checks the To Address.  If it is school.edu I know that it is coming from fetchmail and I assume it is spam and assign it points.  Then I check the from address.  If it is from school.edu I assume it is from fetchmail but is an email I want so I assign it negative points to cancel out the positive.  I have been doing some testing and it seems to be working.  When I download messages from the schools mail server they appear in my postfix mailbox.  Ones that are to my school.edu account and from any other school.edu email account appear normal.
Ones that are to my school.edu email account and from another account (eg. hotmail.com) get tagged, ****SPAM****.  

My only problem is that I don't want them in my mailbox tagged.  I want them deleted.  I have tried increasing the number of points being assigned to them but it doesn't seem to work.  Any ideas what might be going on?

---

