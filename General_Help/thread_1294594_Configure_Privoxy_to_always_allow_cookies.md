---
title: "Configure Privoxy to always allow cookies"
date: 2009-10-18
forum: General Help
---

### Post by Kimm on 2009-10-18
Does anyone know if this is possible?
I'd like my browser to handle cookies, not privoxy (causes to many issues), all I really want it for is to block ads :)

I'm using Chromium btw.

I've googled it, but I get no straight forward hits, all I can find is how to allow cookies for specific domains, not all cookies.

---

### Post by FormerSlacker on 2009-11-06
I just came across this problem. I'm not sure if you solved it, but if you didn't...

Comment out or delete this line in /etc/privoxy/match-all.action:
+session-cookies-only 

And your cookies wont be wiped after every browser restart.

---

### Post by Kimm on 2009-11-06
> **FormerSlacker said:**
> I just came across this problem. I'm not sure if you solved it, but if you didn't...

Comment out or delete this line in /etc/privoxy/match-all.action:
+session-cookies-only 

And your cookies wont be wiped after every browser restart.

Awesome, thanks! :)

---

