---
title: "Postfix not forwarding e-mails properly"
date: 2010-09-09
forum: General Help
---

### Post by JasonSwett on 2010-09-09
I have Postfix set up to forward e-mails to two different addresses. This is my /etc/postfix/virtual:

```

jason@woollymammothlabs.com jason@woollymammothlabs.com, jason.swett@gmail.com

```

I'm forwarding the message back to myself because that's the only way I know if the original message is even getting delivered in the first place.

The problem is that the e-mail isn't making it into my GMail inbox. I've checked my spam folder and it isn't there. And bafflingly, according to the logs, the message does seem to be getting sent:

```
Sep 10 02:34:38 localhost postfix/smtpd[12698]: connect from mail-qw0-f47.google.com[209.85.216.47]
Sep 10 02:34:38 localhost postfix/smtpd[12698]: C14292AB44: client=mail-qw0-f47.google.com[209.85.216.47]
Sep 10 02:34:38 localhost postfix/cleanup[12703]: C14292AB44: message-id=<AANLkTikTXAWvVuFLwDBobMGd+ew_5ETMG_LCv1sTY4sY@mail.gmail.com>
Sep 10 02:34:38 localhost postfix/qmgr[10529]: C14292AB44: from=<jason.swett@gmail.com>, size=2328, nrcpt=2 (queue active)
Sep 10 02:34:38 localhost postfix/local[12704]: C14292AB44: to=<jason@woollymammothlabs.com>, relay=local, delay=0.07, delays=0.06/0.01/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Sep 10 02:34:40 localhost postfix/smtp[12705]: C14292AB44: to=<jason.swett@gmail.com>, orig_to=<jason@woollymammothlabs.com>, relay=gmail-smtp-in.l.google.com[74.125.65.27]:25, delay=1.9, delays=0.06/0.05/0.07/1.7, dsn=2.0.0, status=sent (250 2.0.0 OK 1284086080 s15si17695951ybm.23)
Sep 10 02:34:40 localhost postfix/qmgr[10529]: C14292AB44: removed
Sep 10 02:35:08 localhost postfix/smtpd[12698]: disconnect from mail-qw0-f47.google.com[209.85.216.47]
```

The third-to-last line is what I'm talking about.

Can anyone shed some light on what's going on?

Thanks,
Jason

---

### Post by dcstar on 2010-09-10
> **JasonSwett said:**
> I have Postfix set up to forward e-mails to two different addresses. This is my /etc/postfix/virtual:

```

jason@woollymammothlabs.com jason@woollymammothlabs.com, jason.swett@gmail.com

```

I'm forwarding the message back to myself because that's the only way I know if the original message is even getting delivered in the first place.

The problem is that the e-mail isn't making it into my GMail inbox. I've checked my spam folder and it isn't there. And bafflingly, according to the logs, the message does seem to be getting sent:

```
Sep 10 02:34:38 localhost postfix/smtpd[12698]: connect from mail-qw0-f47.google.com[209.85.216.47]
Sep 10 02:34:38 localhost postfix/smtpd[12698]: C14292AB44: client=mail-qw0-f47.google.com[209.85.216.47]
Sep 10 02:34:38 localhost postfix/cleanup[12703]: C14292AB44: message-id=<AANLkTikTXAWvVuFLwDBobMGd+ew_5ETMG_LCv1sTY4sY@mail.gmail.com>
Sep 10 02:34:38 localhost postfix/qmgr[10529]: C14292AB44: from=<jason.swett@gmail.com>, size=2328, nrcpt=2 (queue active)
Sep 10 02:34:38 localhost postfix/local[12704]: C14292AB44: to=<jason@woollymammothlabs.com>, relay=local, delay=0.07, delays=0.06/0.01/0/0, dsn=2.0.0, status=sent (delivered to maildir)
Sep 10 02:34:40 localhost postfix/smtp[12705]: C14292AB44: to=<jason.swett@gmail.com>, orig_to=<jason@woollymammothlabs.com>, relay=gmail-smtp-in.l.google.com[74.125.65.27]:25, delay=1.9, delays=0.06/0.05/0.07/1.7, dsn=2.0.0, status=sent (250 2.0.0 OK 1284086080 s15si17695951ybm.23)
Sep 10 02:34:40 localhost postfix/qmgr[10529]: C14292AB44: removed
Sep 10 02:35:08 localhost postfix/smtpd[12698]: disconnect from mail-qw0-f47.google.com[209.85.216.47]
```

The third-to-last line is what I'm talking about.

Can anyone shed some light on what's going on?

Thanks,
Jason

Contact Gmail with those log details and ask them.

---

