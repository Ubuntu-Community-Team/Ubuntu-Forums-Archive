---
title: "Postfix + DKIMproxy = Connection Refused by Postfix"
date: 2012-07-29
forum: General Help
---

### Post by Detrol on 2012-07-29
Alright, so i just installed DKIMproxy to my mailserver, and once i try to "telnet domain.com 587" i get Connection Refused, likewise if i try localhost. Though i have come to the conclusion that this snippet of code is the cause of the problem:

```

127.0.0.1:10028 inet  n  -      n       -       10      smtpd
    -o content_filter=
    -o receive_override_options=no_unknown_recipient_checks,no_header_body_checks
    -o smtpd_helo_restrictions=
    -o smtpd_client_restrictions=
    -o smtpd_sender_restrictions=
    -o smtpd_recipient_restrictions=permit_mynetworks,reject
    -o mynetworks=127.0.0.0/8
    -o smtpd_authorized_xforward_hosts=127.0.0.0/8

```

Since if i remove that bit of code, i can connect normaly.

Got any ideas?

Thanks in advance.

---

### Post by Detrol on 2012-07-29
Bump, i would appreciate if anyone have any ideas as quick as possible, i'm kinda in need of it pretty quick.

---

