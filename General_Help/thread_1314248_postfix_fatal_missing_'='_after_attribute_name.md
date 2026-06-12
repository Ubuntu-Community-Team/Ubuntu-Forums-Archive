---
title: "postfix: fatal: missing '=' after attribute name"
date: 2009-11-04
forum: General Help
---

### Post by ninnypants on 2009-11-04
I'm trying to set up my postfix mail server to use dovecot as the Mail Delivery Agent, so I add this line to the postfix main.cf

```

dovecot unix - n n - - pipe
  flags=DRhu user=vmail argv=/user/lib/dovcot/deliver -d ${recipient}

```
When I restart postfix I get this error
```

postfix: fatal: /etc/postfix/main.cf, line 49: missing '=' after attribute name: "dovecot unix - n n - - pipe flags=DRhu user=vmail argv=/user/lib/dovcot/deliver -d ${recipient}

```
I'm using information from here:[http://workaround.org/articles/ispmail-etch/]("http://workaround.org/articles/ispmail-etch/") specifically this section [http://workaround.org/articles/ispmail-etch/#step-5-deliver-emails-through-the-dovecot-lda]("http://workaround.org/articles/ispmail-etch/#step-5-deliver-emails-through-the-dovecot-lda")

---

