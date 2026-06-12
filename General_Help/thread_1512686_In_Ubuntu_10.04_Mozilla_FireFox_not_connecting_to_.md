---
title: "In Ubuntu 10.04 Mozilla FireFox not connecting to the internet while others are."
date: 2010-06-18
forum: General Help
---

### Post by aayushkr on 2010-06-18
Recently, I installed Ubuntu 10.04. Prior to this i had been using Ubuntu 9.10. 

**In 10.04** i am just unable to connect to the net using Mozilla FireFox. But otherwise, Update Manager, Google Chromium are all connecting smoothly. Which implies that there is nothing wrong with my internet connection. 

So now that this is a Mozilla FireFox problem, how do i solve this?

Please Help!

Thanks

---

### Post by dcstar on 2010-06-19
> **aayushkr said:**
> Recently, I installed Ubuntu 10.04. Prior to this i had been using Ubuntu 9.10. 

**In 10.04** i am just unable to connect to the net using Mozilla FireFox. But otherwise, Update Manager, Google Chromium are all connecting smoothly. Which implies that there is nothing wrong with my internet connection. 

So now that this is a Mozilla FireFox problem, how do i solve this?

Please Help!

Thanks

Do a search for disabling IPv6.

---

### Post by aayushkr on 2010-06-19
> **dcstar said:**
> Do a search for disabling IPv6.

Done. Thanks. :KS

IPv6 settings of the internet connection were already disabled. But that of Mozilla FireFox wasn't.  Which is why only FireFox was unable to connect. 

For those who are facing the same problem, the solution to *"FireFox not connecting to internet"* problem is as below:

1> Open Mozilla FireFox,
2> type **about:config** in the URL Locator Box
3> Filter to find **"network.dns.disableIPv6"** 
4> **If** this value is set as **false**, then **Make it true**
5> Restart FireFox and you will be set. 

I was using Ubuntu 9.1(Karmic Koala) for about 3-4 months until yesterday, when i downloaded Ubuntu 10.04 (Lucid Lynx). Its even better!!! **My congratulations to the entire Ubuntu Team!!!**

---

