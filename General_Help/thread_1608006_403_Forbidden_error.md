---
title: "403 Forbidden error"
date: 2010-10-28
forum: General Help
---

### Post by alice06 on 2010-10-28
Hi all

When I open gigapedia, I see this page.
________________________________________________________________
**Forbidden**

  You don't have permission to access / on this server.
  Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
   Apache mod_fcgid/2.3.5 mod_auth_passthrough/2.1 mod_bwlimited/1.4 FrontPage/5.0.2.2635 Server at [www.gigapedia.com]("http://www.gigapedia.com") Port 80 
________________________________________________________________

Earlier it was working fine.
Please help

Alice

---

### Post by yetiman64 on 2010-10-28
Just tried it here and is working OK, see attached screenshot.

What version of Ubuntu are you on and what browser are you using?

If the problem keeps up you can try in terminal,
```
ping -c 5 www.gigapedia.com
``` and check the IP address you are trying to connect to. The result from here is 95.143.192.165. This may help check for network or DNS issues.

---

### Post by alice06 on 2010-10-28
Thanx 

The problem is now solved.

Alice

---

