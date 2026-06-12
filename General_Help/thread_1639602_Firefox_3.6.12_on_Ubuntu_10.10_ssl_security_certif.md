---
title: "Firefox 3.6.12 on Ubuntu 10.10 ssl security certificate error (Comodo certs?)"
date: 2010-12-06
forum: General Help
---

### Post by greenathon on 2010-12-06
Firefox 3.6.12 on Ubuntu 10.10 on my desktop computer is reporting a "this connection is untrusted" error for sites that have security certificates provided by COMODO. Yet, the same sites work fine in Firefox 3.6.x on Windows XP, or Chromium in Ubuntu. Here is the more specific message:

"The certificate is not trusted because the issuer certificate is unknown.

(Error code: sec_error_unknown_issuer)"

The issuer is listed as "COMODO High Assurance Secure Server CA." Here are some examples that throw this error for me:

[http://wingsguate.org/civicrm/contribute/transact?reset=1&id=1](http://wingsguate.org/civicrm/contribute/transact?reset=1&id=1)

[https://contractor.lexisnexis.com/CS/welcome.do?justanswer](https://contractor.lexisnexis.com/CS/welcome.do?justanswer)

It appears that there was some controversy with COMODO  and Mozilla (due to bad behavior by COMODO) in the past, but all I can find on that indicates that this should be not an issue any longer.

Anybody with ideas?

---

### Post by dvdkhlng on 2011-01-22
same problem here, trying to login at [http://www.sipgate.de](http://www.sipgate.de)
Ubuntu 10.10 64-bit.

---

