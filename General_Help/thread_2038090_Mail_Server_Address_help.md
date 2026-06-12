---
title: "Mail Server Address help?"
date: 2012-08-05
forum: General Help
---

### Post by yusufali on 2012-08-05
for an email address
it is in the format of
[email]user@domain.com[/email]

this supports many users, in theory, close to infinite

is it possible
to have an email address in the form of
domain.com

of course this would only work for one user, but in theory, if my name was John Smith, could i have an email set up as 
johnsmith.com

and if so, how would i go about doing so?

---

### Post by Cheesemill on 2012-08-06
It's not possible.

Emails **have** to be of the form user@domain

---

### Post by Habitual on 2012-08-06
n/m. Cheesemill is correct.

---

### Post by SeijiSensei on 2012-08-06
It is possible to configure a mail server so that all mail for user@domain gets dumped into a single mailbox.  Many ISPs offer such a service for their clients with hosting accounts, or you can set up a server using sendmail or Postfix to accomplish the same thing.

---

### Post by Cheesemill on 2012-08-06
Depending on your email provider (or how you set up your email server) you can have all of the email sent to any user at a specific domain forwarded to one account, for example [EMAIL="bob@example.com"]bob@example.com[/EMAIL], [EMAIL="test@example.com"]test@example.com[/EMAIL],  [EMAIL="aghlskdfjgoijvnj@example.com"]aghlskdfjgoijvnj@example.com[/EMAIL] will all end up in the one account that you specify.

This will be the closest that you can get to your desired outcome.

---

### Post by Habitual on 2012-08-06
I was thinking catch-all in post #3, but if Cheesemill says... :)

---

