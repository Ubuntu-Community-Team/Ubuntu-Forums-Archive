---
title: "mail() works in command line but does not in browser"
date: 2011-06-18
forum: General Help
---

### Post by sandino on 2011-06-18
Hi all,

I'm trying to configure sending mail from my site under Ubuntu 10.04 LTS.

I have installed LAMP and postfix. To test mail I created the file test.php with code:

[PHP]
$to      = 'mymail@gmail.com';
$subject = 'The subject';
$message = 'Hello';
$headers = 'From: "My Name" <webmaster@example.com>' . "\r\n" .
    'Reply-To: noreply@example.com' . "\r\n" .
    'X-Mailer: PHP/' . phpversion();

if (mail($to, $subject, $message, $headers)) {
  echo "Mail has been sent to $to\n\r";
} else {
  echo "Mail has NOT been sent\n\r";
}
[/PHP]

This code works fine if run in command line:
```

#php test.php
Mail has been sent to mymail@gmail.com

```
and e-mail is being delivered to my mailbox.

But it does not work if opened in browser, I get:
> Mail has NOT been sent

Does anybody know what's the problem?

---

### Post by sandino on 2011-06-18
Found something interesting in mail.err:

> Jun 18 07:38:37 localhost postfix/sendmail[3100]: fatal: Recipient addresses must be specified on the command line or via the -t option

Where to specify this '-t option' ?

---

