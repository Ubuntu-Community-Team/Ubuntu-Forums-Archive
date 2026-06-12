---
title: "Squid single PC configuration.."
date: 2010-04-03
forum: General Help
---

### Post by karthick87 on 2010-04-03
I have configured squid in a single PC to save bandwidth and to block some sites.It works fine,but the only drawback is if the user disables the proxy settings in the browser they can able to browse all sites..Is there anyway to force all my browsers to go through proxy??

---

### Post by karthick87 on 2010-04-05
Bump for a move..!

---

### Post by dryicebomb on 2010-04-08
yes, but it is a bit more tricky and requires more components than just squid. You could set up a transparent proxy with the help of iptables, here is a good how to for that. [http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

or alternatively you could setup DNS and DHCP on your squid machine and use WPAD. Here is a link from the squid site that explains WPAD some.
[http://wiki.squid-cache.org/SquidFaq/ConfiguringBrowsers#head-5aa28de5e8308087a925cb7ef54ca070a16564d4](http://wiki.squid-cache.org/SquidFaq/ConfiguringBrowsers#head-5aa28de5e8308087a925cb7ef54ca070a16564d4)

Good luck,

---

### Post by karthick87 on 2010-04-11
> **dryicebomb said:**
> yes, but it is a bit more tricky and requires more components than just squid. You could set up a transparent proxy with the help of iptables, here is a good how to for that. [http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html](http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html)

or alternatively you could setup DNS and DHCP on your squid machine and use WPAD. Here is a link from the squid site that explains WPAD some.
[http://wiki.squid-cache.org/SquidFaq/ConfiguringBrowsers#head-5aa28de5e8308087a925cb7ef54ca070a16564d4](http://wiki.squid-cache.org/SquidFaq/ConfiguringBrowsers#head-5aa28de5e8308087a925cb7ef54ca070a16564d4)

Good luck,


All those configurations are for the systems which uses two NIC cards not for single.So can you give me some more information??

---

### Post by gmargo on 2010-04-11
It only takes a few moments with google to find the probable answer on the Squid site:
[http://wiki.squid-cache.org/ConfigExamples/Intercept/IptablesPolicyRoute](http://wiki.squid-cache.org/ConfigExamples/Intercept/IptablesPolicyRoute)

Or all the examples:
[http://wiki.squid-cache.org/ConfigExamples](http://wiki.squid-cache.org/ConfigExamples)

---

