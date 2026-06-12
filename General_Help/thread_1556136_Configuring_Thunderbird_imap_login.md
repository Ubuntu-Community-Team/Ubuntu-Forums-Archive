---
title: "Configuring Thunderbird imap login"
date: 2010-08-19
forum: General Help
---

### Post by the_maplebar on 2010-08-19
This sounds really stupid, but I'm starting at a new job and having trouble configuring thunderbird for the imap server.  I have imap working on my phone so I know my settings are correct and i think I know what the issue is.

user: first.last
imap server; imap.domain.com
smtp server: smtp.domain.com

When I try to connect thunderbird uses the credentials:
[email]first.last@imap.domain.com[/email]

The username should really be 
[email]first.last@domain.com[/email]

But I can't figure out how to correct the user credentials without screwing up the imap url.

---

### Post by anglican on 2010-08-19
> **the_maplebar said:**
> This sounds really stupid, but I'm starting at a new job and having trouble configuring thunderbird for the imap server.  I have imap working on my phone so I know my settings are correct and i think I know what the issue is.

user: first.last
imap server; imap.domain.com
smtp server: smtp.domain.com

When I try to connect thunderbird uses the credentials:
[EMAIL="first.last@imap.domain.com"]first.last@imap.domain.com[/EMAIL]

Thunderbird doesn't do that, it just provides the username "first.last". If your username is actually "first.last@domain.com" then that is what you should enter as "user" and not just "first.last".

> **the_maplebar said:**
> The username should really be 
[EMAIL="first.last@domain.com"]first.last@domain.com[/EMAIL]

But I can't figure out how to correct the user credentials without screwing up the imap url.
Just enter "first.last@domain.com" ... as the username, if that is actually the username needed... (that's how it works with my ISP also).

H

---

