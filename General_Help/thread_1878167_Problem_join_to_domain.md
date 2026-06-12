---
title: "Problem join to domain"
date: 2011-11-09
forum: General Help
---

### Post by Tres_Iqus on 2011-11-09
I get this message when using **sudo domainjoin-cli join midomain administrator **

```

Error: DNS_ERROR_BAD_PACKET [code 0x0000251e]

A bad packet was received from a DNS server. Potentially the requested address
does not exist.


```

windows machines enter the domain without problems

---

### Post by HermanAB on 2011-11-09
So, define the machine address...

This is not a domain issue - but the domain authentication will not work if the DNS is not right.  Test it with nslookup or dig.

---

### Post by Tres_Iqus on 2011-11-09
nslookup and dig give me the correct IP address

---

