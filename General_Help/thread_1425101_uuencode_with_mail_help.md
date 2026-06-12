---
title: "uuencode with mail help"
date: 2010-03-08
forum: General Help
---

### Post by dennismonsewicz on 2010-03-08
I am working with a script that sends out a mail with an attachment by using the uuencode command along with the mail command. But my problem is when I need to run the script using an email address with a dot in the middle of the address (ie. [email]my.name@mail.com[/email])

It breaks at the [dot] in the email address.

Any ideas on how to fix this?

---

### Post by richardjh on 2010-03-08
Have you tried to escape the dot like this:

 ```
my\.name@mail.com
```

Post back the command you are running if this doesn't work.

---

### Post by dennismonsewicz on 2010-03-10
For some reason when I escape the [dot] the command tries to place an email in my local mailbox on the server... it gives me the command no mail for dennismonsewicz

```
uuencode results.xls test.xls | mail -a dennis\.monsewicz@gmail.com

```

Result:
No mail for dennismonsewicz

---

### Post by dcstar on 2010-03-11
> **dennismonsewicz said:**
> For some reason when I escape the [dot] the command tries to place an email in my local mailbox on the server... it gives me the command no mail for dennismonsewicz

```
uuencode results.xls test.xls | mail -a dennis\.monsewicz@gmail.com

```

Result:
No mail for dennismonsewicz

From man mail:

```
     -a      Specify additional header fields on the command line such as "X-
             Loop: foo@bar" etc.  You have to use quotes if the string con&#8208;
             tains spaces.  This argument may be specified more than once, the
             headers will then be concatenated.

```

Why are you using this?

---

### Post by dennismonsewicz on 2010-03-11
I shall have to give using the -a option a try...

I am using this with PHP to send an attachment in an email.

---

