---
title: "forwarding system email thru external Gmail"
date: 2010-01-14
forum: General Help
---

### Post by bobwdn on 2010-01-14
I have configured a command line (9.10) server to forward all the system email notices to an external Gmail account.

All is forwarding fine except, all the emails from root have a return email address of "root <myaccountname@gmail.com>".

I do not think that it is a big security issue but, I would prefer that the root emails were forwarded to an existing user account on the server and then forwarded to my external Gmail account. That way the return address would not say "root" within the address but rather "existinguser <myaccountname@gmail.com".

Anyone have a thought on this? Is exposing the "root" name within the return email address a serious security issue?

---

### Post by amauk on 2010-01-14
I can't see any extra security concern

originating IP address will not change, regardless of which user sends mail to your MTA

I'm assuming no system sensitive info in email (passwords, or the like)

only difference is the word "root" instead of "existinguser" in the From line

---

### Post by bobwdn on 2010-01-14
That is what I was thinking. As the email is forwarded thru my Gmail account and all is password protected, then I did not see it as a big security issue.

Grated, I would prefer "existinguser" but I could not see any harm.

Thanks, amauk for your thoughts.

---

### Post by zalnn on 2010-01-15
you could always create an alias in the /etc/aliases file

eg; root: existinguser

and then forward all the mail that existing user gets to your external email address :)

---

### Post by bobwdn on 2010-01-15
Thanks, zalnn. I tried that and it still sent "root" in the return address. I am going to review what I did this weekend. I might have done something wrong, but I do not think so.

I would just like to get it to say anything but "root".

---

