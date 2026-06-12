---
title: "sendmail and PHP mail, sending from www-data"
date: 2011-04-14
forum: General Help
---

### Post by equinox_ on 2011-04-14
I have specified the following in my PHP code:

```
$to      = 'blah@email.state.edu';
    $subject = 'test';
    $message = 'test';
    $headers = 'From: mail@smartrek.blah.me' . "\r\n" .
               'Reply-To: mail@smartrek.blah.me' . "\r\n" .
                'X-Mailer: PHP/' . phpversion();
mail($to, $subject, $message, $headers);
```

however, for some weird reasons sendmail ignores this From header and instead sends it from www-data@server_name. How do I fix this?

---

### Post by piratebill on 2011-04-14
You might have better luck getting this answered in the programming forum.

---

