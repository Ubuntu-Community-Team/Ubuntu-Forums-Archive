---
title: "dual boot pc joining active directory"
date: 2009-11-29
forum: General Help
---

### Post by arod0405 on 2009-11-29
I'm managing an high school pc lab. I'd like to install ubuntu along with vista in a dual boot setup but I need it to join the school active directory domain.
I know I can use likewise-open but I'm experiencing a few problems.

First joindomain-cli can't resolve domain name. Domain is something like domain.local and I can ping directly any pc in domain with its name (pc01) or FQDN (pc01.domain.local), domain controller included, but I can't resolve domain name. This is not an issue with windows because WINS is used there. How can I fix that? Add some entry in DC's DNS?

Concerning the dual boot setup I guess I should I use a different name and IP address for wista and linux on the same machine. In such a case would some kind of anti-spoofing cause any problems because of the two using the same MAC address?

Last, would you please point me to the right section of the forum if I'm OT here ot to some good documentation about linux integration on AD domain?

Thanks!

---

