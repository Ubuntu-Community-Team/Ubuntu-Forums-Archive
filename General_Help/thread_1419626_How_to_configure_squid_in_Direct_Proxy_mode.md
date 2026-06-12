---
title: "How to configure squid in Direct Proxy mode?"
date: 2010-03-02
forum: General Help
---

### Post by karthick87 on 2010-03-02
I know that squid can be configured in three different modes as Direct Proxy,Reverse Proxy and Transparent Proxy...Can someone tell me the way to configure squid as Direct Proxy??

---

### Post by jpl888 on 2010-03-02
Your question doesn't make a huge amount of sense to me.

By default squid will accept traffic on port 3128 and cache websites for clients that connect on that port.

If you are talking about bypassing the proxy/cache you can configure squid to fetch certain urls direct (instead of caching) but to do that for all sites kind of defeats the point of Squid.

Perhaps you could clarify exactly what you are trying to achieve?

---

