---
title: "dnsbl not working with sendmail (Precise 12.04)"
date: 2012-09-17
forum: General Help
---

### Post by danielsender on 2012-09-17
Hi guys,

Facing an incredible blitz from spammers I decided to add the dnsbl feature in sendmail.mc as:

FEATURE(`dnsbl',`sbl-xbl.spamhaus.org')dnl

after compiling I see that it appears in sendmail.cf

# DNS based IP address spam list sbl-xbl.spamhaus.org
R$*                     $: $&{client_addr}
R$-.$-.$-.$-            $: <?> $(dnsbl $4.$3.$2.$1.sbl-xbl.spamhaus.org. $: OK $)
R<?>OK                  $: OKSOFAR
R<?>$+<TMP>             $: TMPOK
R<?>$+          $#error $@ 5.7.1 $: "550 Rejected: " $&{client_addr} " listed at sbl-xbl.spamhaus.org

and related in other lines. However, after restarting sendmail, when I ran the test I get an email response saying:

Uh-oh, your SBL block is not working!

I wonder if someone has a recipe for fixing this.

Thanks,

Daniel

---

### Post by danielsender on 2012-09-21
any sendmail guru there?

---

### Post by dcstar on 2012-09-21
> **danielsender said:**
> any sendmail guru there?

AFAIK hardly anybody uses sendmail any more, use postfix.

---

### Post by smtp on 2012-09-24
> **dcstar said:**
> AFAIK hardly anybody uses sendmail any more, use postfix.

This is defintely not true. :)

---

### Post by smtp on 2012-09-24
Please try to use zen.spamhaus.org, i.e.:

FEATURE(`dnsbl', `zen.spamhaus.org')dnl

---

### Post by danielsender on 2012-09-24
I did change to zen.spamhaus.org but is still not working.

---

### Post by smtp on 2012-09-28
What do you get in maillog?

---

